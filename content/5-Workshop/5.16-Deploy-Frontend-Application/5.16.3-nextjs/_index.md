---
title : "nextjs"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.16.3</b> "
---

#### 1. Create a Next.js project

##### Step 1: Navigate to the working directory

1. Open **Visual Studio Code**.
2. On the menu bar, select **Terminal** → **New Terminal**.
3. Enter the following command to navigate to the directory where the project will be stored:

```powershell
cd "D:\AWS\New folder\5.16"
```

##### Step 2: Create the Next.js project

1. In the **Terminal** window, run the following command:

```powershell
npx create-next-app@15 energy-waste-dashboard --typescript --eslint --tailwind --src-dir --app --use-npm --import-alias "@/*"
```

2. When the system displays the following question:

```text
Would you like to use Turbopack?
```

3. Select:

```text
Yes
```

4. Wait for the project initialization process to complete.

##### Step 3: Open the project in Visual Studio Code

1. Navigate to the project directory using the following command:

```powershell
cd energy-waste-dashboard
```

2. Open the project in **Visual Studio Code**:

```powershell
code .
```

3. Verify that the path shown in the **Terminal** is:

```text
D:\AWS\New folder\5.16\energy-waste-dashboard
```
![Amplify Source Provider](/images/5-Workshop/5.16/Code1.png)
![Amplify Source Provider](/images/5-Workshop/5.16/Code.png)

---

#### 2. Install the AWS Amplify libraries

##### Step 1: Install the libraries

1. Make sure the **Terminal** is currently in the following directory:

```text
D:\AWS\New folder\5.16\energy-waste-dashboard
```

2. Run the following command to install the **AWS Amplify** libraries:

```powershell
npm install aws-amplify @aws-amplify/ui-react
```

##### Step 2: Verify the installation result

1. If the following warning appears during installation:

```text
npm warn ERESOLVE overriding peer dependency
```

2. But the command still finishes with a message similar to:

```text
added ... packages
```

the libraries have been installed successfully, and you can continue with the next steps.

##### Step 3: Notes on handling dependency warnings

Do not run the following command:

```powershell
npm audit fix --force
```

This command may automatically change dependency versions and cause compatibility issues with **Next.js** or **AWS Amplify**.
![Amplify Source Provider](/images/5-Workshop/5.16/Code3.png)

#### 3. Create local environment variables

##### Step 1: Create the `.env.local` file

1. In the root directory of the **energy-waste-dashboard** project, create a new file named:

```text
.env.local
```

2. The `.env.local` file must be located at the same level as the following files:

```text
package.json
package-lock.json
```
##### Step 2: Add the AWS configuration values

Open the following file:

```text
.env.local
```

Then paste the following content:

```env
NEXT_PUBLIC_AWS_REGION=ap-southeast-1
NEXT_PUBLIC_COGNITO_USER_POOL_ID=ap-southeast-1_OiGmvapoL
NEXT_PUBLIC_COGNITO_CLIENT_ID=42bod21u3a1g499u643mt056fm
NEXT_PUBLIC_API_BASE_URL=https://51ioevkyjc.execute-api.ap-southeast-1.amazonaws.com
```
#### 4. Configure AWS Amplify to connect to Amazon Cognito

##### Step 1: Create the `components` directory

1. In the Visual Studio Code **Explorer**, open the following directory:

```text
src
```

2. Right-click the `src` directory.
3. Select **New Folder**.
4. Name the directory:

```text
components
```

##### Step 2: Create the Amplify configuration file

1. Right-click the following directory:

```text
src/components
```

2. Select **New File**.
3. Name the file:

```text
ConfigureAmplifyClientSide.tsx
```

The full file path is:

```text
src/components/ConfigureAmplifyClientSide.tsx
```

##### Step 3: Add the Cognito configuration code

Open `ConfigureAmplifyClientSide.tsx` and paste the following content:

```tsx
"use client";

import { Amplify } from "aws-amplify";

const userPoolId =
  process.env.NEXT_PUBLIC_COGNITO_USER_POOL_ID;

const userPoolClientId =
  process.env.NEXT_PUBLIC_COGNITO_CLIENT_ID;

if (!userPoolId || !userPoolClientId) {
  throw new Error(
    "The Cognito User Pool ID or App Client ID is missing."
  );
}

Amplify.configure({
  Auth: {
    Cognito: {
      userPoolId,
      userPoolClientId,
      loginWith: {
        email: true,
      },
    },
  },
});

export default function ConfigureAmplifyClientSide() {
  return null;
}
```

Where:

- `userPoolId`: retrieves its value from the `NEXT_PUBLIC_COGNITO_USER_POOL_ID` variable.
- `userPoolClientId`: retrieves its value from the `NEXT_PUBLIC_COGNITO_CLIENT_ID` variable.
- `loginWith.email`: allows users to sign in using their email address.

Do not add the following configuration:

```tsx
{
  ssr: true,
}
```

The application currently handles Cognito authentication directly in the browser.

##### Step 4: Save the file

Press:

```text
Ctrl + S
```

---

#### 5. Configure the application layout

##### Step 1: Open `layout.tsx`

Open the following file:

```text
src/app/layout.tsx
```

##### Step 2: Replace the entire file content

Press:

```text
Ctrl + A
```

Delete the existing content and paste the following code:

```tsx
import type { Metadata } from "next";
import type { ReactNode } from "react";

import "./globals.css";

import ConfigureAmplifyClientSide from "@/components/ConfigureAmplifyClientSide";

export const metadata: Metadata = {
  title: "Energy Waste Dashboard",
  description:
    "Smart Home Energy Waste Monitoring and Alert System",
};

export default function RootLayout({
  children,
}: Readonly<{
  children: ReactNode;
}>) {
  return (
    <html lang="en" suppressHydrationWarning>
      <body>
        <ConfigureAmplifyClientSide />
        {children}
      </body>
    </html>
  );
}
```

Where:

- `metadata.title`: the title displayed on the browser tab.
- `metadata.description`: the application description.
- `ConfigureAmplifyClientSide`: initializes the connection between the frontend and Amazon Cognito.
- `suppressHydrationWarning`: suppresses warnings when a browser extension modifies the HTML before React finishes loading.

##### Step 3: Save the file

Press:

```text
Ctrl + S
```

---

#### 6. Configure the global interface with CSS

##### Step 1: Open `globals.css`

Open the following file:

```text
src/app/globals.css
```

##### Step 2: Replace the entire file content

Press:

```text
Ctrl + A
```

Delete the existing content and paste the following:

```css
@import "tailwindcss";

:root {
  color-scheme: light;
}

html {
  background: #f1f5f9;
}

body {
  min-height: 100vh;
  margin: 0;
  background: #f1f5f9;
  color: #0f172a;
  font-family: Arial, Helvetica, sans-serif;
}

button,
input,
select {
  font: inherit;
}
```

The configuration above performs the following functions:

- Loads Tailwind CSS into the application.
- Sets light mode as the default color scheme.
- Sets the global background color.
- Sets the default text color.
- Sets the font family for the entire page.
- Uses the same font for buttons, input fields, and selection lists.

The final version uses a custom sign-in form, so the following line is not required:

```css
@import "@aws-amplify/ui-react/styles.css";
```

##### Step 3: Save the file

Press:

```text
Ctrl + S
```

---

#### 7. Create a function to retrieve the JWT and call API Gateway

##### Step 1: Create the `lib` directory

1. Right-click the following directory:

```text
src
```

2. Select **New Folder**.
3. Name it:

```text
lib
```

##### Step 2: Create the `api.ts` file

1. Right-click the following directory:

```text
src/lib
```

2. Select **New File**.
3. Name the file:

```text
api.ts
```

The full path is:

```text
src/lib/api.ts
```

##### Step 3: Add the API Gateway request code

Open `api.ts` and paste the following code:

```typescript
import { fetchAuthSession } from "aws-amplify/auth";

const rawApiBaseUrl =
  process.env.NEXT_PUBLIC_API_BASE_URL;

if (!rawApiBaseUrl) {
  throw new Error(
    "NEXT_PUBLIC_API_BASE_URL is missing."
  );
}

const API_BASE_URL = rawApiBaseUrl.replace(
  /\/+$/,
  ""
);

type ApiErrorBody = {
  message?: string;
  error?: string;
};

async function getJwtToken(): Promise<string> {
  let session = await fetchAuthSession();

  let token =
    session.tokens?.idToken?.toString() ??
    session.tokens?.accessToken?.toString();

  if (!token) {
    session = await fetchAuthSession({
      forceRefresh: true,
    });

    token =
      session.tokens?.idToken?.toString() ??
      session.tokens?.accessToken?.toString();
  }

  if (!token) {
    throw new Error(
      "The current session does not contain a JWT. " +
        "Sign out and then sign in again."
    );
  }

  return token;
}

export async function apiGet<T>(
  path: string
): Promise<T> {
  const jwtToken = await getJwtToken();

  const response = await fetch(
    `${API_BASE_URL}${path}`,
    {
      method: "GET",
      headers: {
        Authorization: `Bearer ${jwtToken}`,
        Accept: "application/json",
      },
      cache: "no-store",
    }
  );

  const responseText = await response.text();

  let responseBody: unknown = {};

  if (responseText) {
    try {
      responseBody = JSON.parse(responseText);
    } catch {
      responseBody = {
        message: responseText,
      };
    }
  }

  if (!response.ok) {
    const errorBody =
      responseBody as ApiErrorBody;

    throw new Error(
      errorBody.message ||
        errorBody.error ||
        `The API returned error ${response.status}.`
    );
  }

  return responseBody as T;
}
```

The function above follows this process:

```text
Frontend
→ fetchAuthSession()
→ Retrieve the JWT from the Cognito session
→ Send Authorization: Bearer <JWT>
→ API Gateway JWT Authorizer
→ Lambda API Handler
```

If the current session does not contain a token, the application attempts to refresh the session using:

```typescript
fetchAuthSession({
  forceRefresh: true,
});
```

Do not add the following statement to the source code:

```typescript
console.log(jwtToken);
```

A JWT is authentication information and should not be displayed in the browser Console.

##### Step 4: Save the file

Press:

```text
Ctrl + S
```

---

#### 8. Create the Dashboard interface

##### Step 1: Create the `Dashboard.tsx` file

1. Right-click the following directory:

```text
src/components
```

2. Select **New File**.
3. Name it:

```text
Dashboard.tsx
```

The full path is:

```text
src/components/Dashboard.tsx
```

##### Step 2: Add the Dashboard source code

Open `Dashboard.tsx` and paste the complete code below:

```tsx
"use client";

import {
  useCallback,
  useEffect,
  useState,
} from "react";

import { apiGet } from "@/lib/api";

type DataItem = Record<string, unknown>;

type ListResponse = {
  success?: boolean;
  count?: number;
  roomId?: string;
  items?: DataItem[];
  message?: string;
};

type ReportDetailResponse = {
  success?: boolean;
  item?: DataItem;
  downloadUrl?: string;
  expiresIn?: number;
  message?: string;
};

type DashboardProps = {
  email: string;
  onSignOut: () => Promise<void>;
};

function displayValue(
  value: unknown,
  fallback = "-"
): string {
  if (
    value === null ||
    value === undefined ||
    value === ""
  ) {
    return fallback;
  }

  if (typeof value === "boolean") {
    return value ? "Yes" : "No";
  }

  return String(value);
}

function getRoomId(item: DataItem): string {
  if (typeof item.roomId === "string") {
    return item.roomId;
  }

  if (
    typeof item.PK === "string" &&
    item.PK.startsWith("ROOM#")
  ) {
    return item.PK.replace("ROOM#", "");
  }

  return "lab-01";
}

function getReportDate(
  item: DataItem
): string {
  if (typeof item.date === "string") {
    return item.date;
  }

  if (
    typeof item.SK === "string" &&
    item.SK.startsWith("REPORT#")
  ) {
    return item.SK.replace("REPORT#", "");
  }

  return "";
}

function SummaryCard({
  title,
  value,
  description,
}: {
  title: string;
  value: number | string;
  description: string;
}) {
  return (
    <div className="rounded-2xl border border-slate-200 bg-white p-5 shadow-sm">
      <p className="text-sm font-medium text-slate-500">
        {title}
      </p>

      <p className="mt-2 text-3xl font-bold text-slate-900">
        {value}
      </p>

      <p className="mt-2 text-sm text-slate-500">
        {description}
      </p>
    </div>
  );
}

export default function Dashboard({
  email,
  onSignOut,
}: DashboardProps) {
  const [selectedRoom, setSelectedRoom] =
    useState("lab-01");

  const [rooms, setRooms] =
    useState<DataItem[]>([]);

  const [telemetry, setTelemetry] =
    useState<DataItem[]>([]);

  const [alerts, setAlerts] =
    useState<DataItem[]>([]);

  const [reports, setReports] =
    useState<DataItem[]>([]);

  const [loading, setLoading] =
    useState(true);

  const [error, setError] =
    useState("");

  const [downloadingDate, setDownloadingDate] =
    useState("");

  const loadDashboard = useCallback(
    async () => {
      setLoading(true);
      setError("");

      try {
        const [
          roomsResult,
          telemetryResult,
          alertsResult,
          reportsResult,
        ] = await Promise.all([
          apiGet<ListResponse>("/rooms"),

          apiGet<ListResponse>(
            `/telemetry?roomId=${encodeURIComponent(
              selectedRoom
            )}&limit=20`
          ),

          apiGet<ListResponse>(
            `/alerts?roomId=${encodeURIComponent(
              selectedRoom
            )}&limit=20`
          ),

          apiGet<ListResponse>("/reports"),
        ]);

        const roomItems =
          roomsResult.items ?? [];

        setRooms(roomItems);

        setTelemetry(
          telemetryResult.items ?? []
        );

        setAlerts(
          alertsResult.items ?? []
        );

        setReports(
          reportsResult.items ?? []
        );

        if (
          roomItems.length > 0 &&
          !roomItems.some(
            (room) =>
              getRoomId(room) ===
              selectedRoom
          )
        ) {
          setSelectedRoom(
            getRoomId(roomItems[0])
          );
        }
      } catch (requestError) {
        setError(
          requestError instanceof Error
            ? requestError.message
            : "Unable to load Dashboard data."
        );
      } finally {
        setLoading(false);
      }
    },
    [selectedRoom]
  );

  useEffect(() => {
    void loadDashboard();
  }, [loadDashboard]);

  async function downloadReport(
    report: DataItem
  ) {
    const reportDate =
      getReportDate(report);

    if (!reportDate) {
      setError(
        "The report metadata does not contain a valid date."
      );

      return;
    }

    setDownloadingDate(reportDate);
    setError("");

    const downloadTab = window.open(
      "about:blank",
      "_blank"
    );

    if (downloadTab) {
      downloadTab.opener = null;
    }

    try {
      const result =
        await apiGet<ReportDetailResponse>(
          `/reports/${encodeURIComponent(
            reportDate
          )}`
        );

      if (!result.downloadUrl) {
        throw new Error(
          result.message ||
            "The API did not return a downloadUrl."
        );
      }

      if (downloadTab) {
        downloadTab.location.href =
          result.downloadUrl;
      } else {
        window.location.href =
          result.downloadUrl;
      }
    } catch (requestError) {
      downloadTab?.close();

      setError(
        requestError instanceof Error
          ? requestError.message
          : "Unable to download the report."
      );
    } finally {
      setDownloadingDate("");
    }
  }

  return (
    <div className="min-h-screen bg-slate-100">
      <header className="border-b border-slate-800 bg-slate-950 text-white">
        <div className="mx-auto flex max-w-7xl items-center justify-between px-6 py-5">
          <div>
            <p className="text-xs font-semibold uppercase tracking-[0.2em] text-emerald-400">
              AWS Serverless Project
            </p>

            <h1 className="mt-1 text-xl font-bold">
              Smart Home Energy Waste Monitoring
            </h1>
          </div>

          <div className="flex items-center gap-4">
            <div className="hidden text-right sm:block">
              <p className="text-sm font-medium">
                {email}
              </p>

              <p className="text-xs text-slate-400">
                Cognito authenticated
              </p>
            </div>

            <button
              type="button"
              onClick={() => void onSignOut()}
              className="rounded-lg border border-slate-600 px-4 py-2 text-sm font-medium hover:bg-slate-800"
            >
              Sign out
            </button>
          </div>
        </div>
      </header>

      <main className="mx-auto max-w-7xl space-y-8 px-6 py-8">
        <section className="flex flex-col justify-between gap-4 rounded-2xl bg-emerald-700 p-6 text-white shadow-lg md:flex-row md:items-center">
          <div>
            <h2 className="text-2xl font-bold">
              Energy Monitoring Dashboard
            </h2>

            <p className="mt-2 text-sm text-emerald-50">
              Monitor energy usage, detect waste,
              and view daily reports.
            </p>
          </div>

          <div className="flex flex-wrap items-center gap-3">
            <label
              htmlFor="room"
              className="text-sm font-medium"
            >
              Room:
            </label>

            <select
              id="room"
              value={selectedRoom}
              onChange={(event) =>
                setSelectedRoom(
                  event.target.value
                )
              }
              className="rounded-lg bg-white px-4 py-2 text-sm text-slate-900"
            >
              {rooms.length === 0 && (
                <option value="lab-01">
                  lab-01
                </option>
              )}

              {rooms.map((room, index) => {
                const roomId =
                  getRoomId(room);

                return (
                  <option
                    key={`${roomId}-${index}`}
                    value={roomId}
                  >
                    {displayValue(
                      room.roomName ??
                        room.name ??
                        roomId
                    )}
                  </option>
                );
              })}
            </select>

            <button
              type="button"
              onClick={() =>
                void loadDashboard()
              }
              className="rounded-lg bg-white px-4 py-2 text-sm font-semibold text-emerald-700"
            >
              Refresh
            </button>
          </div>
        </section>

        {error && (
          <div className="rounded-xl border border-red-200 bg-red-50 p-4 text-sm text-red-700">
            {error}
          </div>
        )}

        <section className="grid gap-4 md:grid-cols-2 xl:grid-cols-4">
          <SummaryCard
            title="Rooms"
            value={rooms.length}
            description="Configured rooms"
          />

          <SummaryCard
            title="Telemetry"
            value={telemetry.length}
            description="20 most recent records"
          />

          <SummaryCard
            title="Alerts"
            value={alerts.length}
            description="Recent alerts"
          />

          <SummaryCard
            title="Reports"
            value={reports.length}
            description="Generated reports"
          />
        </section>

        {loading ? (
          <div className="rounded-2xl bg-white p-10 text-center text-slate-500 shadow-sm">
            Loading data from API Gateway...
          </div>
        ) : (
          <>
            <section className="rounded-2xl bg-white shadow-sm">
              <div className="border-b border-slate-200 px-6 py-4">
                <h2 className="text-lg font-bold">
                  Latest telemetry
                </h2>
              </div>

              <div className="overflow-x-auto">
                <table className="min-w-full text-left text-sm">
                  <thead className="bg-slate-50 text-slate-600">
                    <tr>
                      <th className="px-6 py-3">
                        Time
                      </th>
                      <th className="px-6 py-3">
                        Device
                      </th>
                      <th className="px-6 py-3">
                        Power
                      </th>
                      <th className="px-6 py-3">
                        Status
                      </th>
                      <th className="px-6 py-3">
                        Occupancy
                      </th>
                      <th className="px-6 py-3">
                        Waste
                      </th>
                    </tr>
                  </thead>

                  <tbody className="divide-y divide-slate-100">
                    {telemetry.map(
                      (item, index) => (
                        <tr
                          key={displayValue(
                            item.SK,
                            String(index)
                          )}
                        >
                          <td className="whitespace-nowrap px-6 py-3">
                            {displayValue(
                              item.timestamp
                            )}
                          </td>

                          <td className="px-6 py-3">
                            {displayValue(
                              item.deviceName ??
                                item.deviceId
                            )}
                          </td>

                          <td className="px-6 py-3 font-medium">
                            {displayValue(
                              item.powerW
                            )}{" "}
                            W
                          </td>

                          <td className="px-6 py-3">
                            {displayValue(
                              item.deviceStatus
                            )}
                          </td>

                          <td className="px-6 py-3">
                            {displayValue(
                              item.occupancy
                            )}
                          </td>

                          <td className="px-6 py-3">
                            {displayValue(
                              item.isWaste
                            )}
                          </td>
                        </tr>
                      )
                    )}

                    {telemetry.length === 0 && (
                      <tr>
                        <td
                          colSpan={6}
                          className="px-6 py-8 text-center text-slate-500"
                        >
                          No telemetry data is available.
                        </td>
                      </tr>
                    )}
                  </tbody>
                </table>
              </div>
            </section>

            <section className="rounded-2xl bg-white shadow-sm">
              <div className="border-b border-slate-200 px-6 py-4">
                <h2 className="text-lg font-bold">
                  Energy waste alerts
                </h2>
              </div>

              <div className="overflow-x-auto">
                <table className="min-w-full text-left text-sm">
                  <thead className="bg-slate-50 text-slate-600">
                    <tr>
                      <th className="px-6 py-3">
                        Time
                      </th>
                      <th className="px-6 py-3">
                        Device
                      </th>
                      <th className="px-6 py-3">
                        Power
                      </th>
                      <th className="px-6 py-3">
                        Details
                      </th>
                    </tr>
                  </thead>

                  <tbody className="divide-y divide-slate-100">
                    {alerts.map(
                      (item, index) => (
                        <tr
                          key={displayValue(
                            item.SK,
                            String(index)
                          )}
                        >
                          <td className="whitespace-nowrap px-6 py-3">
                            {displayValue(
                              item.timestamp
                            )}
                          </td>

                          <td className="px-6 py-3">
                            {displayValue(
                              item.deviceName ??
                                item.deviceId
                            )}
                          </td>

                          <td className="px-6 py-3 font-medium text-red-600">
                            {displayValue(
                              item.powerW
                            )}{" "}
                            W
                          </td>

                          <td className="px-6 py-3">
                            {displayValue(
                              item.message ??
                                item.reason ??
                                "Energy waste detected"
                            )}
                          </td>
                        </tr>
                      )
                    )}

                    {alerts.length === 0 && (
                      <tr>
                        <td
                          colSpan={4}
                          className="px-6 py-8 text-center text-slate-500"
                        >
                          No alerts are available.
                        </td>
                      </tr>
                    )}
                  </tbody>
                </table>
              </div>
            </section>

            <section className="rounded-2xl bg-white shadow-sm">
              <div className="border-b border-slate-200 px-6 py-4">
                <h2 className="text-lg font-bold">
                  Energy reports
                </h2>
              </div>

              <div className="overflow-x-auto">
                <table className="min-w-full text-left text-sm">
                  <thead className="bg-slate-50 text-slate-600">
                    <tr>
                      <th className="px-6 py-3">
                        Date
                      </th>
                      <th className="px-6 py-3">
                        Telemetry
                      </th>
                      <th className="px-6 py-3">
                        Alerts
                      </th>
                      <th className="px-6 py-3">
                        Energy
                      </th>
                      <th className="px-6 py-3">
                        Average power
                      </th>
                      <th className="px-6 py-3">
                        Action
                      </th>
                    </tr>
                  </thead>

                  <tbody className="divide-y divide-slate-100">
                    {reports.map(
                      (item, index) => {
                        const reportDate =
                          getReportDate(item);

                        return (
                          <tr
                            key={
                              reportDate ||
                              String(index)
                            }
                          >
                            <td className="px-6 py-3 font-medium">
                              {displayValue(
                                reportDate
                              )}
                            </td>

                            <td className="px-6 py-3">
                              {displayValue(
                                item.telemetryCount
                              )}
                            </td>

                            <td className="px-6 py-3">
                              {displayValue(
                                item.alertCount
                              )}
                            </td>

                            <td className="px-6 py-3">
                              {displayValue(
                                item.totalEnergyKwh
                              )}{" "}
                              kWh
                            </td>

                            <td className="px-6 py-3">
                              {displayValue(
                                item.averagePowerW
                              )}{" "}
                              W
                            </td>

                            <td className="px-6 py-3">
                              <button
                                type="button"
                                onClick={() =>
                                  void downloadReport(
                                    item
                                  )
                                }
                                disabled={
                                  downloadingDate ===
                                  reportDate
                                }
                                className="rounded-lg bg-slate-900 px-4 py-2 text-xs font-semibold text-white disabled:opacity-50"
                              >
                                {downloadingDate ===
                                reportDate
                                  ? "Generating URL..."
                                  : "Download JSON"}
                              </button>
                            </td>
                          </tr>
                        );
                      }
                    )}

                    {reports.length === 0 && (
                      <tr>
                        <td
                          colSpan={6}
                          className="px-6 py-8 text-center text-slate-500"
                        >
                          No reports are available.
                        </td>
                      </tr>
                    )}
                  </tbody>
                </table>
              </div>
            </section>
          </>
        )}
      </main>
    </div>
  );
}
```

The Dashboard calls the following APIs:

```text
GET /rooms
GET /telemetry
GET /alerts
GET /reports
GET /reports/{date}
```

##### Step 3: Save the file

Press:

```text
Ctrl + S
```

---

#### 9. Create the Amazon Cognito sign-in page

##### Step 1: Open `page.tsx`

Open the following file:

```text
src/app/page.tsx
```

##### Step 2: Delete the default content

Press:

```text
Ctrl + A
```

Delete all existing content.

##### Step 3: Add the sign-in source code

Paste the complete code below:

```tsx
"use client";

import {
  useEffect,
  useState,
  type FormEvent,
} from "react";

import {
  fetchAuthSession,
  getCurrentUser,
  signIn,
  signOut,
} from "aws-amplify/auth";

import Dashboard from "@/components/Dashboard";

type SignedInUser = {
  username: string;
  userId: string;
  email: string;
};

async function loadValidUser(): Promise<SignedInUser> {
  const session = await fetchAuthSession();

  const idToken =
    session.tokens?.idToken?.toString();

  const accessToken =
    session.tokens?.accessToken?.toString();

  if (!idToken && !accessToken) {
    throw new Error("SESSION_HAS_NO_TOKEN");
  }

  const currentUser =
    await getCurrentUser();

  const emailClaim =
    session.tokens?.idToken?.payload.email;

  return {
    username: currentUser.username,
    userId: currentUser.userId,
    email:
      typeof emailClaim === "string"
        ? emailClaim
        : currentUser.username,
  };
}

async function clearInvalidSession(): Promise<void> {
  try {
    await signOut();
  } catch {
    // Always return the interface to the sign-in page.
  }
}

export default function Home() {
  const [email, setEmail] =
    useState("");

  const [password, setPassword] =
    useState("");

  const [user, setUser] =
    useState<SignedInUser | null>(null);

  const [checkingSession, setCheckingSession] =
    useState(true);

  const [loading, setLoading] =
    useState(false);

  const [error, setError] =
    useState("");

  useEffect(() => {
    async function checkSession() {
      try {
        const currentUser =
          await loadValidUser();

        setUser(currentUser);
      } catch {
        await clearInvalidSession();
        setUser(null);
      } finally {
        setCheckingSession(false);
      }
    }

    void checkSession();
  }, []);

  async function handleSubmit(
    event: FormEvent<HTMLFormElement>
  ) {
    event.preventDefault();

    setLoading(true);
    setError("");

    try {
      await clearInvalidSession();

      const result = await signIn({
        username:
          email.trim().toLowerCase(),
        password,
        options: {
          authFlowType: "USER_AUTH",
          preferredChallenge: "PASSWORD",
        },
      });

      if (
        !result.isSignedIn ||
        result.nextStep.signInStep !== "DONE"
      ) {
        throw new Error(
          `Cognito requires the following next step: ${result.nextStep.signInStep}`
        );
      }

      const currentUser =
        await loadValidUser();

      setUser(currentUser);
      setPassword("");
    } catch (requestError) {
      await clearInvalidSession();
      setUser(null);

      setError(
        requestError instanceof Error
          ? requestError.message
          : "Unable to sign in."
      );
    } finally {
      setLoading(false);
    }
  }

  async function handleSignOut() {
    setUser(null);
    setEmail("");
    setPassword("");
    setError("");

    try {
      await signOut();
    } catch {
      // The interface still returns to the sign-in page.
    }
  }

  if (checkingSession) {
    return (
      <main className="flex min-h-screen items-center justify-center bg-slate-100">
        <p className="text-slate-600">
          Checking the sign-in session...
        </p>
      </main>
    );
  }

  if (user) {
    return (
      <Dashboard
        email={user.email}
        onSignOut={handleSignOut}
      />
    );
  }

  return (
    <main className="flex min-h-screen items-center justify-center bg-slate-100 p-6">
      <form
        onSubmit={handleSubmit}
        className="w-full max-w-sm rounded-2xl bg-white p-7 shadow-lg"
      >
        <p className="text-sm font-semibold uppercase tracking-wider text-emerald-600">
          AWS Serverless Project
        </p>

        <h1 className="mt-2 text-2xl font-bold text-slate-900">
          Sign in
        </h1>

        <p className="mt-2 text-sm text-slate-500">
          Smart Home Energy Waste Monitoring
        </p>

        <label
          htmlFor="email"
          className="mt-6 block text-sm font-medium text-slate-700"
        >
          Email
        </label>

        <input
          id="email"
          type="email"
          autoComplete="username"
          value={email}
          onChange={(event) =>
            setEmail(event.target.value)
          }
          required
          className="mt-2 w-full rounded-lg border border-slate-300 px-4 py-2 outline-none focus:border-emerald-600"
        />

        <label
          htmlFor="password"
          className="mt-4 block text-sm font-medium text-slate-700"
        >
          Password
        </label>

        <input
          id="password"
          type="password"
          autoComplete="current-password"
          value={password}
          onChange={(event) =>
            setPassword(event.target.value)
          }
          required
          className="mt-2 w-full rounded-lg border border-slate-300 px-4 py-2 outline-none focus:border-emerald-600"
        />

        {error && (
          <div className="mt-4 rounded-lg border border-red-200 bg-red-50 p-3 text-sm text-red-700">
            {error}
          </div>
        )}

        <button
          type="submit"
          disabled={loading}
          className="mt-5 w-full rounded-lg bg-emerald-700 px-4 py-2 font-semibold text-white hover:bg-emerald-600 disabled:cursor-not-allowed disabled:opacity-60"
        >
          {loading
            ? "Signing in..."
            : "Sign in"}
        </button>
      </form>
    </main>
  );
}
```

The application signs in using the following configuration:

```typescript
authFlowType: "USER_AUTH",
preferredChallenge: "PASSWORD",
```

After Cognito authenticates the user successfully, the application checks for:

```text
ID Token
Access Token
```

If neither token is available, the application does not display the Dashboard.

##### Step 4: Save all source code files

In Visual Studio Code, select:

```text
File
→ Save All
```

Alternatively, press:

```text
Ctrl + K
S
```
Once completed, push the source code to GitHub.

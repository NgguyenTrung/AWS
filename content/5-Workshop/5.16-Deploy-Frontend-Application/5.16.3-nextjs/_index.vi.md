---
title : "nextjs"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.16.3</b> "
---
#### 1. Tạo project Next.js

##### Bước 1: Chuyển đến thư mục làm việc

1. Mở **Visual Studio Code**.
2. Trên thanh menu, chọn **Terminal** → **New Terminal**.
3. Nhập lệnh sau để chuyển đến thư mục lưu project:

```powershell
cd "D:\AWS\New folder\5.16"
```

##### Bước 2: Tạo project Next.js

1. Tại cửa sổ **Terminal**, chạy lệnh:

```powershell
npx create-next-app@15 energy-waste-dashboard --typescript --eslint --tailwind --src-dir --app --use-npm --import-alias "@/*"
```

2. Khi hệ thống hiển thị câu hỏi:

```text
Would you like to use Turbopack?
```

3. Chọn:

```text
Yes
```

4. Chờ quá trình khởi tạo project hoàn tất.

##### Bước 3: Mở project trong Visual Studio Code

1. Chuyển vào thư mục project bằng lệnh:

```powershell
cd energy-waste-dashboard
```

2. Mở project bằng **Visual Studio Code**:

```powershell
code .
```

3. Kiểm tra đường dẫn trong **Terminal** phải là:

```text
D:\AWS\New folder\5.16\energy-waste-dashboard
```
![Amplify Source Provider](/images/5-Workshop/5.16/Code1.png)
![Amplify Source Provider](/images/5-Workshop/5.16/Code.png)

---

#### 2. Cài thư viện AWS Amplify

##### Bước 1: Cài đặt thư viện

1. Đảm bảo **Terminal** đang đứng tại thư mục:

```text
D:\AWS\New folder\5.16\energy-waste-dashboard
```

2. Chạy lệnh sau để cài đặt thư viện **AWS Amplify**:

```powershell
npm install aws-amplify @aws-amplify/ui-react
```

##### Bước 2: Kiểm tra kết quả cài đặt

1. Nếu quá trình cài đặt xuất hiện cảnh báo:

```text
npm warn ERESOLVE overriding peer dependency
```

2. Nhưng lệnh vẫn kết thúc bằng thông báo tương tự:

```text
added ... packages
```

thì các thư viện đã được cài đặt thành công và có thể tiếp tục thực hiện các bước tiếp theo.

##### Bước 3: Lưu ý khi xử lý cảnh báo dependency

Không chạy lệnh:

```powershell
npm audit fix --force
```

Lệnh này có thể tự động thay đổi phiên bản của các dependency và gây lỗi tương thích với **Next.js** hoặc **AWS Amplify**.
![Amplify Source Provider](/images/5-Workshop/5.16/Code3.png)

#### 3. Tạo Environment Variables trên máy

##### Bước 1: Tạo file `.env.local`

1. Tại thư mục gốc của project **energy-waste-dashboard**, tạo một file mới có tên:

```text
.env.local
```

2. File `.env.local` phải nằm cùng cấp với các file:

```text
package.json
package-lock.json
```
##### Bước 2: Điền thông tin cấu hình AWS

Mở file:

```text
.env.local
```

Sau đó dán nội dung sau:

```env
NEXT_PUBLIC_AWS_REGION=ap-southeast-1
NEXT_PUBLIC_COGNITO_USER_POOL_ID=ap-southeast-1_OiGmvapoL
NEXT_PUBLIC_COGNITO_CLIENT_ID=42bod21u3a1g499u643mt056fm
NEXT_PUBLIC_API_BASE_URL=https://51ioevkyjc.execute-api.ap-southeast-1.amazonaws.com
```
#### 4. Cấu hình AWS Amplify kết nối Amazon Cognito

##### Bước 1: Tạo thư mục `components`

1. Trong cửa sổ **Explorer** của Visual Studio Code, mở thư mục:

```text
src
```

2. Nhấn chuột phải vào thư mục `src`.
3. Chọn **New Folder**.
4. Đặt tên thư mục:

```text
components
```

##### Bước 2: Tạo file cấu hình Amplify

1. Nhấn chuột phải vào thư mục:

```text
src/components
```

2. Chọn **New File**.
3. Đặt tên file:

```text
ConfigureAmplifyClientSide.tsx
```

Đường dẫn đầy đủ của file:

```text
src/components/ConfigureAmplifyClientSide.tsx
```

##### Bước 3: Thêm mã nguồn cấu hình Cognito

Mở file `ConfigureAmplifyClientSide.tsx` và dán nội dung sau:

```tsx
"use client";

import { Amplify } from "aws-amplify";

const userPoolId =
  process.env.NEXT_PUBLIC_COGNITO_USER_POOL_ID;

const userPoolClientId =
  process.env.NEXT_PUBLIC_COGNITO_CLIENT_ID;

if (!userPoolId || !userPoolClientId) {
  throw new Error(
    "Thiếu Cognito User Pool ID hoặc App Client ID."
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

Trong đó:

- `userPoolId`: lấy giá trị từ biến `NEXT_PUBLIC_COGNITO_USER_POOL_ID`.
- `userPoolClientId`: lấy giá trị từ biến `NEXT_PUBLIC_COGNITO_CLIENT_ID`.
- `loginWith.email`: cho phép người dùng đăng nhập bằng địa chỉ email.

Không thêm cấu hình:

```tsx
{
  ssr: true,
}
```

Ứng dụng hiện xử lý đăng nhập Cognito trực tiếp ở phía trình duyệt.

##### Bước 4: Lưu file

Nhấn:

```text
Ctrl + S
```

---

#### 5. Cấu hình Layout của ứng dụng

##### Bước 1: Mở file `layout.tsx`

Mở file:

```text
src/app/layout.tsx
```

##### Bước 2: Thay toàn bộ nội dung file

Nhấn:

```text
Ctrl + A
```

Xóa nội dung cũ và dán mã sau:

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
    <html lang="vi" suppressHydrationWarning>
      <body>
        <ConfigureAmplifyClientSide />
        {children}
      </body>
    </html>
  );
}
```

Trong đó:

- `metadata.title`: tên hiển thị trên tab trình duyệt.
- `metadata.description`: mô tả của ứng dụng.
- `ConfigureAmplifyClientSide`: khởi tạo kết nối giữa frontend và Amazon Cognito.
- `suppressHydrationWarning`: hạn chế cảnh báo khi tiện ích trình duyệt thay đổi HTML trước khi React hoàn tất quá trình tải.

##### Bước 3: Lưu file

Nhấn:

```text
Ctrl + S
```

---

#### 6. Cấu hình giao diện chung bằng CSS

##### Bước 1: Mở file `globals.css`

Mở file:

```text
src/app/globals.css
```

##### Bước 2: Thay toàn bộ nội dung file

Nhấn:

```text
Ctrl + A
```

Xóa nội dung cũ và dán:

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

Cấu hình trên thực hiện các chức năng:

- Nạp Tailwind CSS vào ứng dụng.
- Đặt giao diện mặc định ở chế độ sáng.
- Thiết lập màu nền chung.
- Thiết lập màu chữ mặc định.
- Thiết lập phông chữ cho toàn bộ trang.
- Đồng bộ phông chữ giữa nút, ô nhập liệu và danh sách lựa chọn.

Bản cuối sử dụng form đăng nhập tự xây dựng nên không cần thêm dòng:

```css
@import "@aws-amplify/ui-react/styles.css";
```

##### Bước 3: Lưu file

Nhấn:

```text
Ctrl + S
```

---

#### 7. Tạo hàm lấy JWT và gọi API Gateway

##### Bước 1: Tạo thư mục `lib`

1. Nhấn chuột phải vào thư mục:

```text
src
```

2. Chọn **New Folder**.
3. Đặt tên:

```text
lib
```

##### Bước 2: Tạo file `api.ts`

1. Nhấn chuột phải vào thư mục:

```text
src/lib
```

2. Chọn **New File**.
3. Đặt tên file:

```text
api.ts
```

Đường dẫn đầy đủ:

```text
src/lib/api.ts
```

##### Bước 3: Thêm mã nguồn gọi API Gateway

Mở file `api.ts` và dán:

```typescript
import { fetchAuthSession } from "aws-amplify/auth";

const rawApiBaseUrl =
  process.env.NEXT_PUBLIC_API_BASE_URL;

if (!rawApiBaseUrl) {
  throw new Error(
    "Thiếu NEXT_PUBLIC_API_BASE_URL."
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
      "Phiên đăng nhập không có JWT. " +
        "Hãy đăng xuất và đăng nhập lại."
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
        `API trả về lỗi ${response.status}.`
    );
  }

  return responseBody as T;
}
```

Hàm trên hoạt động theo quy trình:

```text
Frontend
→ fetchAuthSession()
→ Lấy JWT từ phiên Cognito
→ Gửi Authorization: Bearer <JWT>
→ API Gateway JWT Authorizer
→ Lambda API Handler
```

Nếu phiên hiện tại chưa có token, ứng dụng thử làm mới phiên bằng:

```typescript
fetchAuthSession({
  forceRefresh: true,
});
```

Không thêm lệnh sau vào mã nguồn:

```typescript
console.log(jwtToken);
```

JWT là thông tin xác thực và không nên hiển thị trong Console của trình duyệt.

##### Bước 4: Lưu file

Nhấn:

```text
Ctrl + S
```

---

#### 8. Tạo giao diện Dashboard

##### Bước 1: Tạo file `Dashboard.tsx`

1. Nhấn chuột phải vào thư mục:

```text
src/components
```

2. Chọn **New File**.
3. Đặt tên:

```text
Dashboard.tsx
```

Đường dẫn đầy đủ:

```text
src/components/Dashboard.tsx
```

##### Bước 2: Thêm mã nguồn Dashboard

Mở file `Dashboard.tsx` và dán toàn bộ mã sau:

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
    return value ? "Có" : "Không";
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
            : "Không thể tải dữ liệu Dashboard."
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
        "Metadata báo cáo không có ngày hợp lệ."
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
            "API không trả về downloadUrl."
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
          : "Không thể tải báo cáo."
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
              Đăng xuất
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
              Theo dõi điện năng, cảnh báo lãng phí
              và báo cáo hằng ngày.
            </p>
          </div>

          <div className="flex flex-wrap items-center gap-3">
            <label
              htmlFor="room"
              className="text-sm font-medium"
            >
              Phòng:
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
              Làm mới
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
            description="Phòng đã cấu hình"
          />

          <SummaryCard
            title="Telemetry"
            value={telemetry.length}
            description="20 mẫu gần nhất"
          />

          <SummaryCard
            title="Alerts"
            value={alerts.length}
            description="Cảnh báo gần nhất"
          />

          <SummaryCard
            title="Reports"
            value={reports.length}
            description="Báo cáo đã tạo"
          />
        </section>

        {loading ? (
          <div className="rounded-2xl bg-white p-10 text-center text-slate-500 shadow-sm">
            Đang tải dữ liệu từ API Gateway...
          </div>
        ) : (
          <>
            <section className="rounded-2xl bg-white shadow-sm">
              <div className="border-b border-slate-200 px-6 py-4">
                <h2 className="text-lg font-bold">
                  Telemetry gần nhất
                </h2>
              </div>

              <div className="overflow-x-auto">
                <table className="min-w-full text-left text-sm">
                  <thead className="bg-slate-50 text-slate-600">
                    <tr>
                      <th className="px-6 py-3">
                        Thời gian
                      </th>
                      <th className="px-6 py-3">
                        Thiết bị
                      </th>
                      <th className="px-6 py-3">
                        Công suất
                      </th>
                      <th className="px-6 py-3">
                        Trạng thái
                      </th>
                      <th className="px-6 py-3">
                        Có người
                      </th>
                      <th className="px-6 py-3">
                        Lãng phí
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
                          Chưa có telemetry.
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
                  Cảnh báo lãng phí
                </h2>
              </div>

              <div className="overflow-x-auto">
                <table className="min-w-full text-left text-sm">
                  <thead className="bg-slate-50 text-slate-600">
                    <tr>
                      <th className="px-6 py-3">
                        Thời gian
                      </th>
                      <th className="px-6 py-3">
                        Thiết bị
                      </th>
                      <th className="px-6 py-3">
                        Công suất
                      </th>
                      <th className="px-6 py-3">
                        Nội dung
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
                                "Phát hiện lãng phí điện"
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
                          Chưa có cảnh báo.
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
                  Báo cáo điện năng
                </h2>
              </div>

              <div className="overflow-x-auto">
                <table className="min-w-full text-left text-sm">
                  <thead className="bg-slate-50 text-slate-600">
                    <tr>
                      <th className="px-6 py-3">
                        Ngày
                      </th>
                      <th className="px-6 py-3">
                        Telemetry
                      </th>
                      <th className="px-6 py-3">
                        Alerts
                      </th>
                      <th className="px-6 py-3">
                        Điện năng
                      </th>
                      <th className="px-6 py-3">
                        Công suất TB
                      </th>
                      <th className="px-6 py-3">
                        Thao tác
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
                                  ? "Đang tạo URL..."
                                  : "Tải JSON"}
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
                          Chưa có báo cáo.
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

Dashboard gọi các API sau:

```text
GET /rooms
GET /telemetry
GET /alerts
GET /reports
GET /reports/{date}
```

##### Bước 3: Lưu file

Nhấn:

```text
Ctrl + S
```

---

#### 9. Tạo trang đăng nhập Amazon Cognito

##### Bước 1: Mở file `page.tsx`

Mở file:

```text
src/app/page.tsx
```

##### Bước 2: Xóa nội dung mặc định

Nhấn:

```text
Ctrl + A
```

Xóa toàn bộ nội dung cũ.

##### Bước 3: Thêm mã nguồn đăng nhập

Dán toàn bộ mã sau:

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
    // Luôn đưa giao diện về trang đăng nhập.
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
          `Cognito yêu cầu bước tiếp theo: ${result.nextStep.signInStep}`
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
          : "Không thể đăng nhập."
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
      // Giao diện vẫn quay về trang đăng nhập.
    }
  }

  if (checkingSession) {
    return (
      <main className="flex min-h-screen items-center justify-center bg-slate-100">
        <p className="text-slate-600">
          Đang kiểm tra phiên đăng nhập...
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
          Đăng nhập
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
            ? "Đang đăng nhập..."
            : "Sign in"}
        </button>
      </form>
    </main>
  );
}
```

Ứng dụng đăng nhập bằng cấu hình:

```typescript
authFlowType: "USER_AUTH",
preferredChallenge: "PASSWORD",
```

Sau khi Cognito xác thực thành công, ứng dụng kiểm tra:

```text
ID Token
Access Token
```

Nếu không có cả hai token, ứng dụng không hiển thị Dashboard.

##### Bước 4: Lưu toàn bộ source code

Trong Visual Studio Code, chọn:

```text
File
→ Save All
```

Hoặc nhấn:

```text
Ctrl + K
S
```
Xong đưa Github

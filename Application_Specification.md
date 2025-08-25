
## Application Specification

>用途：描述產出。它定義了這個專案有哪些規格文件、它們在哪裡、以及它們的內容是什麼。它回答的是「What」的問題（我們有哪些規格？）

This project follows a Spec-driven development methodology. All specifications for behavior, APIs, and design are located in the `/spec` and `/docs` directories.
  - 本專案採用規格驅動開發；行為、API 與設計的規格皆位於 `/spec` 與 `/docs`。

- **Design & Documentation (`/docs`)**: The `/docs` directory contains all high-level project documentation, including product requirements (`prd.md`), detailed feature designs, and architectural diagrams. This serves as the central repository for understanding the project's goals and architecture.
  - `/docs` 包含產品需求、功能設計與架構圖，是理解專案目標與架構的中樞。

  為了讓結構更清晰，`/docs` 目錄的組織方式如下：

  - **產品需求文件 (位於 `/docs/prd.md`)**:
    - 作為整個專案的最高層級文件，定義了產品的目標、功能規格與業務場景，是理解專案「為何做」與「做什麼」的起點。

  - **高階設計文件 (位於 `/docs/designs`)**:
    - 針對一個完整、獨立的功能模組，內容較宏觀，描述整個功能的技術選型、實作策略、路由、中介軟體、前後端如何配合等。
    - 可視為某個大功能的「**總體設計藍圖**」。

  - **流程圖與實作細節 (位於 `/docs/diagrams`)**:
    - 針對一個更具體的流程或頁面，內容更聚焦於細節。
    - **流程圖 (`flow-*.md`)**: 使用 Mermaid.js 語法，描繪使用者操作的每一步或後端處理的環節。
    - **頁面設計 (`*_design.md`)**: 描述某個頁面的元件構成、數據傳遞與開發挑戰。
    - 可視為總體設計藍圖下的「**詳細施工圖**」。

- **Technical Specifications (`/spec`)**: This directory contains detailed technical specifications, broken down as follows:
  - `/spec` 存放技術規格，並依下列子目錄劃分：
    - `acceptance/`: Defines the criteria for when a feature is considered complete.
      - 定義功能何時視為完成的驗收標準。
    - `api/`: Contains the OpenAPI contract (`api.yaml`) and related API test cases.
      - 包含 OpenAPI 合約（`api.yaml`）與相關 API 測試案例。
    - `database/`: Holds the database schema definition (`schema.yaml`).
      - 資料庫結構定義（`schema.yaml`）。
    - `errors/`: Defines standardized error codes and formats (`error-codes.yaml`).
      - 標準化錯誤碼與格式（`error-codes.yaml`）。
    - `features/`: Contains user-facing feature descriptions written in Gherkin (`.feature` files).
      - 以 Gherkin 撰寫的使用者情境（`.feature` 檔）。
    - `format/`: Specifies standard data structures, such as the format for error responses.
      - 標準資料結構規格（例如錯誤回應格式）。
    - `validation/`: Contains all data validation rules for different models (e.g., `beer-validation.yaml`).
      - 各模型的資料驗證規則（如 `beer-validation.yaml`）。

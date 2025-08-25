
## Contribution Guidelines

>用途：規範流程。它定義了開發者在為這個專案貢獻(contribute) 時，應該遵循的步驟、慣例和規則。它回答的是「How」的問題（我們該如何開發？）

### 0. Feature Proposal - 功能提案

#### Before Starting Development
- **Discuss**: Share your idea in team chat/meeting first
  - 討論：先在團隊聊天/會議中分享你的想法
- **Spec Review**: Ensure the feature aligns with project goals
  - 規格審查：確保功能符合專案目標
- **Scope Definition**: Define clear acceptance criteria
  - 範圍定義：定義清楚的驗收標準
- **Approval**: Get team consensus before starting implementation
  - 批准：在開始實作前獲得團隊共識

#### Proposal Template
```markdown
## Feature Request: [簡潔的功能名稱]

### Problem Statement
What problem does this feature solve?

### Proposed Solution
Brief description of the proposed solution

### Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

### Impact Assessment
- **Effort**: Low/Medium/High
- **Priority**: Low/Medium/High
- **Dependencies**: Any blocking items?

### Alternative Solutions Considered
What other approaches were considered?
```

### 1. Development Process - 開發流程

#### Feature Development Workflow

To maintain clarity, code quality, and avoid duplicate work, please follow this comprehensive process for every feature.
為維持清晰、品質並避免重工，請依此流程開發每個功能。

**Quick Reference - 快速參考**:
```
0. 💡 Propose → 1. 📋 Plan & Spec → 2. 🧪 Write Test → 3. 💻 Write Code → 4. ✅ Refactor → 5. 📝 Update Status → 6. 🚀 Commit & PR
```

**Detailed Steps - 詳細步驟**:

**1. Before You Start: Specification & Planning**
開始前請先確認規格並完成規劃。

Before writing any code, ensure the groundwork is laid out.
在動手寫程式前，先把基礎準備好。

-   **Check for Existing Scenarios**: Review `spec/features/` to ensure a similar feature or scenario doesn't already exist.
    - 檢查 `spec/features/`，避免重複現有情境或功能。
-   **Consult the Schema**: Refer to `spec/database/schema.yaml` to understand the required data structures.
    - 參考 `spec/database/schema.yaml` 理解資料結構需求。
-   **Prepare Migrations**: Ensure a corresponding database migration file exists in `database/migrations/` for any new tables or columns.
    - 為新表或欄位準備對應的遷移檔於 `database/migrations/`。

**2. During Development: Test-Driven Development**
開發過程中採用測試驅動開發。

Follow TDD principles: write tests first, then implement the minimal code to pass.
遵循 TDD 原則：先寫測試，再實作最小程式碼通過測試。

- **Red Phase**: Write a failing test that describes the desired behavior
  - 紅燈階段：撰寫描述期望行為的失敗測試
- **Green Phase**: Write minimal code to make the test pass
  - 綠燈階段：撰寫最小程式碼讓測試通過
- **Refactor Phase**: Clean up the code while keeping tests green
  - 重構階段：清理程式碼但保持測試通過

**3. During Development: Track Your Progress**
開發過程中要持續追蹤並更新進度。

As you work on the feature, keep the team informed by updating its status.
開發時請即時更新狀態，讓團隊知悉進度。

-   **Update Feature Status**: In the corresponding `.feature` file, update the status using the table format below:
    - 在對應的 `.feature` 檔，使用以下表格格式更新狀態：

    ```gherkin
    # 1. Status: TODO | IN_PROGRESS | DONE
    # 2. Design: docs/diagrams/your-feature-flow.md
    # 3. Test: tests/Feature/YourSpecificTest.php
    # 4. Scenario Status Tracking:
    # | Scenario Name                    | Status        | Test Method                    | UI  | Backend |
    # |----------------------------------|---------------|--------------------------------|-----|---------|
    # | Scenario 1 description          | DONE          | test_scenario_1                | DONE| DONE    |
    # | Scenario 2 description          | IN_PROGRESS   | test_scenario_2                | DONE| TODO    |
    # | Scenario 3 description          | TODO          | test_scenario_3                | TODO| TODO    |
    ```
    -   **`# Status`**: The overall status of the feature.
        - 整體狀態：TODO（待開始）、IN_PROGRESS（進行中）、DONE（已完成）
    -   **`# Design`**: Link to the design document or diagram.
        - 設計文件或流程圖連結
    -   **`# Test`**: Link to the primary test file.
        - 主要測試檔連結
    -   **`# UI`**: The development status of the UI.
        - UI 開發狀態：TODO（待開始）、IN_PROGRESS（進行中）、DONE（已完成）
    -   **`# Backend`**: The development status of the backend logic.
        - 後端開發狀態：TODO（待開始）、IN_PROGRESS（進行中）、DONE（已完成）
    -   **Scenario Status Tracking**: Table format for tracking individual scenario progress.
        - 情境狀態追蹤：表格格式用於追蹤個別情境進度。

> **重要提示**: 新增 `Scenario` 時，請務必在上方加上一行 `# 場景: ...` 的中文註解，以方便團隊成員快速理解。

**4. During Development: Add Test Coverage Documentation**
開發過程中要加上測試覆蓋文件。

As you write tests, document the relationship between test classes and spec scenarios.
撰寫測試時，請記錄測試類別與規格場景的對應關係。

-   **Add Test Class Documentation**: In each test class, add comprehensive documentation above the class declaration using the following format:
    - 在每個測試類別上方，使用以下格式加上完整的文件註解：

    ```php
    /**
     * @covers \spec\features\feature_name\scenario_name.feature
     * 
     * Scenarios covered:
     * - Scenario 1 description
     * - Scenario 2 description
     * 
     * Test coverage:
     * - Specific functionality tested
     * - API endpoints covered
     * - Database operations verified
     */
    class YourTestClass extends TestCase
    ```

    This documentation helps developers understand:
    - 此文件註解幫助開發者理解：
    -   **Which spec scenarios are covered** by the test class
        - 測試類別覆蓋了哪些規格場景
    -   **What specific functionality** is being tested
        - 測試了哪些具體功能
    -   **The relationship** between tests and specifications
        - 測試與規格之間的關係

**5. Before You Finish: Definition of Done & Quality Checks**
完成前請確認 DoD 與品質檢查是否滿足。

Before a feature can be considered complete and ready for review, it must meet all the following criteria.
功能在送審前必須符合以下所有條件。

-   **Run All Tests**: Before every `git commit`, run the entire automated test suite with code coverage.
    - 每次 `git commit` 前都要執行完整自動化測試並產生覆蓋率。
    - **Minimum Coverage**: 80% for new features, 90% for critical paths
    - **最低覆蓋率**: 新功能 80%，關鍵路徑 90%
    ```bash
    # From the HoldYourBeer project root:
    php artisan test --coverage
    
    # For specific test files:
    php artisan test --coverage --filter=YourTestClass
    
    # For coverage report in Laradock:
    docker-compose -f laradock/docker-compose.yml exec -w /var/www workspace php artisan test --coverage
    ```
    > **注意**: 在 Laradock 環境中，請參考 `laradock_setting.md` 了解完整的指令執行方式。
-   **Ensure All Tests Pass**: Only commit if all tests report a `PASS` status.
    - 僅在所有測試皆通過時才進行提交。
-   **Git Workflow**: Follow conventional commit format and branch naming.
    - **Git 工作流程**: 遵循常規提交格式與分支命名。
    ```bash
    # Branch naming convention:
    git checkout -b feature/beer-tracking
    git checkout -b bugfix/login-validation
    git checkout -b hotfix/security-patch
    
    # Commit message format:
    git commit -m "feat: add beer tasting history tracking"
    git commit -m "fix: resolve authentication token expiration issue"
    git commit -m "docs: update API documentation for beer endpoints"
    ```

-   **Final Checklist (Definition of Done)**:
    - 完成檢查清單：
    -   [ ] Corresponding `.feature` file exists and is reviewed.
        - 對應的 `.feature` 檔已存在且完成審閱。
    -   [ ] API specification in `spec/api/api.yaml` updated if needed.
        - 必要時已更新 `spec/api/api.yaml`。
    -   [ ] Design & documentation in `/docs` updated if needed.
        - 必要時已更新 `/docs` 內的設計與文件。
    -   [ ] Unit tests (Pest/PHPUnit) are written and passing.
        - 單元測試（Pest/PHPUnit）已撰寫並通過。
    -   [ ] Behavior tests (Behat) for the feature file are passing.
        - 行為測試（Behat）通過。
    -   [ ] API contract tests (Dredd) are passing.
        - API 合約測試（Dredd）通過。
    -   [ ] Responsive design works on mobile, tablet, and desktop.
        - 響應式設計在手機、平板、桌機皆正常。
    -   [ ] CI/CD pipeline is green.
        - CI/CD pipeline 全綠。
    -   [ ] Code has been peer-reviewed and merged to main.
        - 程式碼已完成同儕審查並合併至 main。

> **Note**: This project uses **PCOV** for code coverage analysis. The `--coverage` flag will generate a text report directly in your terminal after the tests run.
> 本專案使用 **PCOV** 進行覆蓋率分析；加入 `--coverage` 會在終端機輸出報告。

> **Advanced Tip**: Consider setting up a Git pre-commit hook to automate this testing process. This is a great way to enforce code quality automatically.
> 建議設定 Git pre-commit hook 自動執行測試，以自動化維持程式碼品質。

### 2. Code Standards - 程式碼標準

#### Coding Conventions
- **PHP Standards**: Follow PSR-12 coding standards
  - 遵循 PSR-12 程式碼標準
- **Laravel Conventions**: Use Laravel naming conventions and best practices
  - 使用 Laravel 命名慣例與最佳實踐
- **Database**: Use snake_case for table/column names, singular table names
  - 資料庫：表名/欄位名使用 snake_case，表名使用單數形式

#### File Organization
- **Controllers**: Place in appropriate namespace (`App\Http\Controllers\Api\` for API)
  - 控制器：放在適當的命名空間（API 放在 `App\Http\Controllers\Api\`）
- **Models**: Use singular form, place in `App\Models\`
  - 模型：使用單數形式，放在 `App\Models\`
- **Tests**: Mirror the application structure in `tests/Feature/` and `tests/Unit/`
  - 測試：在 `tests/Feature/` 和 `tests/Unit/` 中鏡像應用程式結構

### 3. Pull Request Guidelines - PR 指南

#### Before Submitting
- **Branch**: Ensure your branch is up-to-date with main
  - 分支：確保你的分支與 main 同步
- **Tests**: All tests must pass with coverage requirements met
  - 測試：所有測試必須通過且滿足覆蓋率要求
- **Documentation**: Update relevant documentation and specs
  - 文件：更新相關文件與規格

#### PR Template
```markdown
## Description
Brief description of the changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
- [ ] Unit tests added/updated
- [ ] Feature tests added/updated
- [ ] All tests passing
- [ ] Coverage requirements met

## Checklist
- [ ] Code follows project standards
- [ ] Self-review completed
- [ ] Documentation updated
- [ ] Spec files updated if needed
```

### 4. Review Process - 審查流程

#### Code Review Requirements
- **Minimum Reviewers**: At least 1 team member approval required
  - **最少審查者**: 至少需要 1 位團隊成員批准
- **Response Time**: Reviewers should respond within 24 hours
  - **回應時間**: 審查者應在 24 小時內回應
- **Merge Policy**: No direct merges to main; all changes go through PR
  - **合併政策**: 禁止直接合併到 main；所有變更都需通過 PR

#### Review Checklist
- [ ] Code follows established patterns
- [ ] Tests are comprehensive and meaningful
- [ ] Error handling is appropriate
- [ ] Performance considerations addressed
- [ ] Security implications reviewed

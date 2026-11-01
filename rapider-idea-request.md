<!-- Rapider Official App SOW & Specification | App #170: Restaurant Management & Kitchen Operations (restaurant-management-and-kitchen-operations) | Domain: HSP -->

# #170 Restaurant Management & Kitchen Operations (`restaurant-management-and-kitchen-operations`) — Scope of Work (SOW)

- **App Number & Name:** `#170` — Restaurant Management & Kitchen Operations
- **Proposed App Key:** `restaurant-management-and-kitchen-operations`
- **Suite / Domain Key & Model Prefix:** `HSP` (`Hsp*`)
- **Function Category:** 18. Hospitality, Restaurants & Travel
- **Representative Product (`P1`):** Toast
- **Combined Feature Catalog:** [../combined-features/170-restaurant-management-and-kitchen-operations-features.md](../combined-features/170-restaurant-management-and-kitchen-operations-features.md)
- **Target Release Posture:** Omnichannel F&B Menu Engineering, Multi-Course Dining Checks, Synchronized Multi-Station KDS, Delivery Aggregation & Kitchen Safety Microapplication

---

## 1. Executive Outcome & Target Audience

### 1.1 Business Problem Solved
Restaurants, cafes, bars, hotel F&B outlets, and ghost kitchens lose margin and guest trust when front-of-house ordering, third-party delivery tablets, and back-of-house kitchen stations operate in silos—resulting in servers selling `86`'d dishes, entrees dying under heat lamps waiting on side stations, manual delivery re-keying errors, untracked post-fire kitchen waste, and disputed tip-pool spreadsheets. **Rapider Restaurant Management & Kitchen Operations (`restaurant-management-and-kitchen-operations`)** unifies daypart menu engineering, nested modifiers and allergen flags, seat-and-course dining check orchestration, synchronized multi-station Prep & Expeditor (`Expo`) Kitchen Display Systems (KDS), tablet-free delivery order throttling, HACCP food-safety logs, and server tip-pool reconciliation natively connected to Rapider `pos`, `payments`, `acc`, `inventory`, `payroll`, `#169` Hotel PMS, `#171` Reservations, and `#175` Food Costing.

### 1.2 Target Personas & Progressive Disclosure
- **SME Fast-Path Defaults (Independent Restaurants, Cafes, Food Trucks, Bars):** Launch in under 15 minutes with a single menu + modifier library, unified Dine-In/Takeout check pad, single-screen Prep + Expo `<rapider-kanban>` KDS with *All-Day* item counts, instant one-tap `86` stockouts, and automated end-of-shift sales & tip summary.
- **Enterprise Progressive Disclosure (Multi-Unit Restaurant Groups, Fine-Dining Venues, Hotel F&B Directors, Ghost Kitchens):** Unlock brand-inherited regional menus, multi-course hold/fire & synchronized station cook-time pacing (`GRILL` + `FRY` + `GARDE_MANGER` + `EXPO`), dynamic 3rd-party delivery prep-time throttling, hotel guest charge-to-room posting (`#169`), HACCP cooler/line temperature compliance gates, loss-prevention post-fire void approvals via Home `WorkItem`s, and automated USALI/F&B `FinJournalEntry` postings.

### 1.3 Measurable Business Outcomes
- **Zero Sold-Out (`86`) Order Rejections:** Real-time countdown & `86` state propagates across server handhelds, tabletop QR, and 3rd-party delivery channels in under 2 seconds.
- **25% Reduction in Ticket Bump Times & Remakes:** Synchronized cook-time delayed firing and structured allergen/modifier tickets align multi-station plating on the Expo pass while cutting kitchen remake waste.
- **100% Auditable Void, Waste & Tip-Pool Integrity:** Distinguishing pre-fire cancellations from post-fire spoilage feeds exact `PMIX`/waste events into `#175` Food Costing and reconciles `Decimal128` server/bar/kitchen tip pools directly to `payroll`.

### 1.4 Benchmark Summary (`P1`–`P6`)
Synthesizes the high-velocity KDS *All-Day* grid, live `86` countdowns, and restaurant check/tip workflows of **`P1` Toast**, Prep-vs-Expo separation and omnichannel delivery aggregation of **`P2` Square for Restaurants**, multi-venue menu inheritance and hotel room-charge handoff of **`P3` Lightspeed K-Series**, synchronized station cook-time pacing and enterprise loss prevention of **`P4` Oracle MICROS Simphony**, POS-to-KDS-to-ERP inventory synergy of **`P5` Odoo Restaurant**, and dynamic kitchen load throttling plus HACCP compliance of **`P6` Microsoft Dynamics 365 (LS Central)**.

---

## 2. In-Scope, Out-of-Scope & Suite Ownership Boundaries

### 2.1 In-Scope Capabilities
1. Multi-outlet daypart menus (`HspRestaurantMenu`), menu items (`HspMenuItem`), nested forced/optional modifier groups (`HspModifierGroup`), combo/prix-fixe bundles, allergen badges, and live `86` / portion countdown controls.
2. Service-mode dining checks (`HspDiningCheck`) supporting seat numbers, multi-course hold/fire (`DRINKS`, `APPS`, `MAINS`, `DESSERT`), split-by-seat/item/fraction, tabletop QR tab append, pre-fire vs. post-fire void/comp reason codes, and tender handoff to `pos` (`ComPosTransaction`) or `#169` Hotel PMS folio.
3. Multi-station Prep & Master Expeditor (`Expo`) Kitchen Display System (`HspKitchenStation`, `HspKitchenTicket`) with synchronized cook-time delayed firing, *All-Day* aggregated counts, color SLA timers, bump/recall, and station failover routing.
4. Tablet-free 1st-party (`ComSite`) and 3rd-party delivery webhook normalization, dynamic kitchen load prep-time throttling, and Expo bag/tamper-seal verification.
5. Digital opening/closing & HACCP temperature line-check logs (`HspKitchenSafetyLog`), server shift checkout & weighted tip-pool allocations (`HspTipPoolAllocation`), daily outlet Z-read GL summaries, and real-time `PMIX`/waste event emission.

### 2.2 Out-of-Scope Capabilities (Delegated to Adjacent Rapider Apps)
- **Online restaurant table booking widgets, guest dining waitlists, SMS table-ready quotes, and host floor-plan seating:** Owned by `#171 Restaurant Reservations & Table Management` (`restaurant-reservations-and-table-management`).
- **Sub-recipe yield conversions, supplier AP invoice OCR/line-cost tracking, and theoretical vs. actual food-cost variance:** Owned by `#175 Restaurant Food Cost & Recipe Management` (`restaurant-food-cost-and-recipe-management`).
- **Payment terminal card EMV/NFC capture and raw retail cash-drawer ledger:** Owned by built `payments` (`FinPaymentIntent`) and `pos` (`ComPosTransaction`).
- **Employee shift scheduling, timeclocks, and statutory tax withholding:** Owned by built `HR` apps (`employees`, `attendance`, `payroll`).

### 2.3 Cross-Suite Ownership & Integration Contract

| Domain / App | Owns (Canonical Models) | Integration Contract with `restaurant-management-and-kitchen-operations` |
| :--- | :--- | :--- |
| **`restaurant-management-and-kitchen-operations` (`#170` — This App)** | `HspRestaurantOutlet`, `HspRestaurantMenu`, `HspMenuItem`, `HspModifierGroup`, `HspDiningCheck`, `HspKitchenStation`, `HspKitchenTicket`, `HspKitchenSafetyLog`, `HspTipPoolAllocation` | Owns F&B menu execution, seat/course check lifecycle, multi-station KDS pacing, delivery aggregation, HACCP logs, and tip-pool calculation. |
| **`restaurant-reservations-and-table-management` (`#171` — HSP)** | `HspDiningFloorTable`, `HspDiningReservation`, `HspWaitlistEntry` | Emits `hsp.table.party_seated` (carrying table ID, party size, VIP/allergy notes) to auto-open `HspDiningCheck`, and consumes `#170` check progression (`MAINS_FIRED`, `CHECK_PAID`) to update live host turn-time predictions. |
| **`restaurant-food-cost-and-recipe-management` (`#175` — HSP)** | `HspRecipe`, `HspIngredientSpec`, `HspFoodCostVariance` | Consumes `#170` `hsp.restaurant.pmix_recorded` and `hsp.restaurant.waste_logged` events to calculate theoretical recipe depletion and plate margin alerts. |
| **`hotel-property-management-system-pms` (`#169` — HSP)** | `HspHotelReservation`, `HspGuestFolio` | `#170` queries checked-in hotel guests and invokes `hsp.pms.postRoomChargeFromPos` to settle dining checks onto guest folios. |
| **`pos` & `productcatalog` (`COM` Suite)** | `ComPosTransaction`, `ComProduct` | `HspMenuItem` maps to `ComProduct`; check settlement generates/links `ComPosTransaction` and processes card tenders via `FinPaymentIntent`. |
| **`payments`, `acc`, `accpayable` (`FIN` Suite)** | `FinPaymentIntent`, `FinJournalEntry`, `FinSupplierBill` | Card tips/captures settle via `FinPaymentIntent`; daily Z-reads post `FinJournalEntry`; 3rd-party delivery commissions accrue toward `FinSupplierBill`. |
| **`attendance` & `payroll` (`HR` Suite)** | `HrEmployee`, `HrAttendancePunch`, `HrPayrollRun` | `HspTipPoolAllocation` reads `HrAttendancePunch` worked hours by role and pushes approved tip payouts to `payroll`. |
| **Rapider Platform Services** | Identity/RBAC, Home `WorkItem`, `projectChannelMessage`, Kafka/OpenWhisk | High-value post-fire voids/comps & HACCP temperature excursions create Home `WorkItem`s; pre-shift 86/specials lineups run in `projectChannelMessage`. |

---

## 3. Primary Web Pages & Sidebar Navigation Architecture

To comply strictly with the **Rapider Minimum 3 Items Sidebar Rule**, all visible pages are grouped into **3 sidebar sections (`Overview`, `Kitchen & Service`, `Governance`) containing 3 visible items each (9 visible menu items total)**. Detail views and creation/edit drawers set `displayOnMenu: false`.

| # | Route | Page Title | Sidebar Section | Menu Visible | Key Components & UX |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `dashboard` | Restaurant Pulse | `Overview` | `true` (Order 1) | Live KPI cards (`countSWR`): Net F&B Sales, Open Checks, Avg KDS Bump Time, Active `86` Items, Delivery Throttle Status, daypart sales curve. |
| 2 | `dining-checks` | Open Checks & Service Pad | `Overview` | `true` (Order 2) | Live `HspDiningCheck` ledger (`DINE_IN`, `BAR_TAB`, `TAKEOUT`, `DELIVERY_3P`) via `findSWR`, `#activeFilterTagsBar` with `Clear all`, course status badges, clickable check `#CHK-...` -> `check-detail`. |
| 3 | `eighty-six-board` | Live 86 & Countdown Control | `Overview` | `true` (Order 3) | Instant stockout & remaining-portion countdown board (`HspMenuItem` / `HspModifierGroup`) with one-tap `86` / `Restore` sync across POS, QR, and delivery. |
| 4 | `kds-board` | Kitchen Display (Prep & Expo) | `Kitchen & Service` | `true` (Order 4) | High-contrast `<rapider-kanban>` KDS (`WAITING_TO_FIRE`, `PREPARING`, `PLATING_EXPO`, `READY_FOR_RUNNER`), station selector (`ALL_EXPO`, `GRILL`, `FRY`, `SAUTE`, `BAR`), *All-Day* aggregated item sidebar, SLA color timers, one-tap Bump & Recall. |
| 5 | `delivery-hub` | Delivery & Online Throttle | `Kitchen & Service` | `true` (Order 5) | Unified 1st/3rd-party delivery queue, courier ETA badges, `<rapider-phone-input>` customer/driver lookup, dynamic prep-time quote slider & rush throttle controls. |
| 6 | `menus-modifiers` | Menus, Dayparts & Modifiers | `Kitchen & Service` | `true` (Order 6) | `HspRestaurantMenu`, `HspMenuItem`, and `HspModifierGroup` catalog with daypart schedules, allergen chips, station routing, and cook-time seconds config. |
| 7 | `haccp-safety` | HACCP & Line Checklists | `Governance` | `true` (Order 7) | Opening/closing checklists and `HspKitchenSafetyLog` cooler/hot-hold temperature table with out-of-range danger highlights and corrective action logs. |
| 8 | `tip-pools-zread` | Shift Z-Read & Tip Pools | `Governance` | `true` (Order 8) | Daily outlet Z-read reconciliation, `HspTipPoolAllocation` calculator by `HrAttendancePunch` hours/points, `FinJournalEntry` & `payroll` export status. |
| 9 | `voids-speed-audit` | Voids, Comps & Speed Analytics | `Governance` | `true` (Order 9) | Loss-prevention audit of pre-fire vs. post-fire voids/comps (`MADE_WAS_WASTED`), pending manager approval indicators, and station p50/p90 speed-of-service charts. |
| 10 | `check-detail` | Dining Check & Course Cockpit | *(Hidden)* | `false` | Full `HspDiningCheck` workspace (`?id=...`): seat/course matrix, `Fire Course` triggers, split-check builder, POS/Hotel Room-Charge settlement, AI pairing hints (`projectChannelMessage`), `Back to list`. |
| 11 | `menu-detail` | Menu & Modifier Workspace | *(Hidden)* | `false` | Deep editor for a `HspRestaurantMenu` (`?id=...`) showing sections, nested `HspModifierGroup` min/max rules, outlet price overrides, and `PMIX` popularity badges. |
| 12 | `menu-item-drawer` | Create / Edit Menu Item | *(Hidden)* | `false` | Sliding drawer configuring `Decimal128` price, prep station, target cook time (seconds), allergen flags, portion countdown, `try/catch/finally` save reset, auto-close. |
| 13 | `safety-log-drawer` | Log Line Temperature / Void Request | *(Hidden)* | `false` | Sliding drawer to record equipment temperatures (auto-triggering Home `WorkItem` on critical excursion) or submit post-fire comp/void with mandatory reason code. |

---

## 4. Canonical Data Models (`Hsp*` — 9 Models)

All models omit `projectId`, use platform UUIDs (`00000000-xxxx-xxxx-xxxx-xxxxxxxxxxxx` in seed data), enforce optimistic `version`, and store all prices, upcharges, tax amounts, comps, and tip shares as `Decimal128`.

| Model Name | Key Fields & Types | Relationships & External Refs | Invariants & Lifecycle |
| :--- | :--- | :--- | :--- |
| **`HspRestaurantOutlet`** | `code` (String, unique), `name` (String), `conceptType` (`FULL_SERVICE`, `QSR_FAST_CASUAL`, `BAR_LOUNGE`, `HOTEL_FB`, `GHOST_KITCHEN`), `timezone` (String), `currencyCode` (String), `defaultQuoteMinutes` (Int), `throttleMode` (`NORMAL`, `EXTENDED_PREP`, `PAUSED_3P`), `phone` (String E.164), `status` (`OPEN`, `CLOSED_SHIFT`, `ARCHIVED`) | `propertyId` -> `HspProperty.id` (optional for hotel F&B), `locationId` -> `HrLocation.id`, `legalEntityId` -> `FinLegalEntity.id` | Controls active kitchen quote times and hotel PMS room-charge eligibility. |
| **`HspRestaurantMenu`** | `code` (String), `name` (String), `daypart` (`ALL_DAY`, `BREAKFAST`, `BRUNCH`, `LUNCH`, `HAPPY_HOUR`, `DINNER`, `LATE_NIGHT`), `activeDaysOfWeek` (Int[]), `startTime` (String), `endTime` (String), `channels` (String[]), `isPublished` (Boolean) | `outletId` -> `HspRestaurantOutlet.id`, `parentMasterMenuId` -> `HspRestaurantMenu.id` (optional brand inheritance) | `endTime` window validated per daypart; unpublished changes never affect live KDS/QR menus until published. |
| **`HspMenuItem`** | `sku` (String), `name` (String), `kitchenShortName` (String), `categoryName` (String), `defaultCourse` (`DRINKS`, `COURSE_1_APPS`, `COURSE_2_MAINS`, `COURSE_3_DESSERT`), `basePrice` (`Decimal128`), `targetCookSeconds` (Int), `allergens` (String[]), `availabilityStatus` (`AVAILABLE`, `COUNTDOWN`, `EIGHTY_SIXED`), `remainingPortions` (Int, nullable) | `menuId` -> `HspRestaurantMenu.id`, `primaryStationId` -> `HspKitchenStation.id`, `productId` -> `ComProduct.id`, `modifierGroupIds` -> `HspModifierGroup.id[]`, `recipeId` -> `HspRecipe.id` (`#175`) | When `availabilityStatus == COUNTDOWN` and `remainingPortions` decrements to `0`, transitions atomically to `EIGHTY_SIXED`. |
| **`HspModifierGroup`** | `name` (String), `selectionRule` (`FORCED_EXACT`, `FORCED_MIN_MAX`, `OPTIONAL`), `minSelections` (Int), `maxSelections` (Int), `allowPrefixes` (Boolean: `NO`, `LIGHT`, `EXTRA`, `ON_SIDE`), `options` (JSON array of `{ code, label, upchargeAmount: Decimal128, allergens, isEightySixed }`) | `outletId` -> `HspRestaurantOutlet.id` | Order line cannot be fired if any `FORCED_*` group violates `minSelections <= count <= maxSelections`. |
| **`HspKitchenStation`** | `code` (String), `name` (String), `stationRole` (`PREP_LINE`, `BAR`, `MASTER_EXPO`, `CUSTOMER_READY_BOARD`), `warningThresholdSeconds` (Int), `overdueThresholdSeconds` (Int), `isOnline` (Boolean) | `outletId` -> `HspRestaurantOutlet.id`, `fallbackStationId` -> `HspKitchenStation.id` (nullable) | If `isOnline == false`, incoming items route deterministically to `fallbackStationId` (never dropped). |
| **`HspDiningCheck`** | `checkNumber` (String, unique), `serviceMode` (`DINE_IN`, `BAR_TAB`, `COUNTER_QSR`, `TAKEOUT`, `QR_TABLE`, `DELIVERY_3P`), `externalDeliveryRef` (String), `tableLabel` (String), `guestCount` (Int), `guestPhone` (String E.164), `allergyAlertBanner` (String), `lines` (JSON array with `seatNo`, `course`, `menuItemId`, `modifiers`, `fireState`, `voidState`, `lineNetAmount: Decimal128`), `subtotalAmount` (`Decimal128`), `compTotalAmount` (`Decimal128`), `taxAmount` (`Decimal128`), `tipAmount` (`Decimal128`), `grandTotalAmount` (`Decimal128`), `status` (`OPEN`, `COURSES_FIRING`, `CHECK_PRESENTED`, `PARTIALLY_PAID`, `PAID_CLOSED`, `CHARGED_TO_ROOM`, `VOIDED`) | `outletId` -> `HspRestaurantOutlet.id`, `serverEmployeeId` -> `HrEmployee.id`, `diningReservationId` -> `HspDiningReservation.id` (`#171`), `posTransactionIds` -> `ComPosTransaction.id[]`, `hotelFolioChargeId` -> `HspFolioCharge.id` (`#169`) | `grandTotalAmount == subtotalAmount - compTotalAmount + taxAmount + tipAmount`; split child checks preserve exact `Decimal128` sum invariance; closed checks are immutable. |
| **`HspKitchenTicket`** | `ticketNumber` (String), `course` (`DRINKS`, `COURSE_1_APPS`, `COURSE_2_MAINS`, `COURSE_3_DESSERT`), `isRushRefire` (Boolean), `scheduledFireAt` (DateTime), `firedAt` (DateTime), `startedAt` (DateTime), `bumpedAt` (DateTime), `actualCookSeconds` (Int), `slaState` (`ON_TIME`, `WARNING`, `OVERDUE`), `status` (`WAITING_TO_FIRE`, `PREPARING`, `PLATING_EXPO`, `READY_FOR_RUNNER`, `DELIVERED_BUMPED`, `RECALLED`) | `outletId` -> `HspRestaurantOutlet.id`, `diningCheckId` -> `HspDiningCheck.id`, `stationId` -> `HspKitchenStation.id` | Synchronized pacing sets `scheduledFireAt = maxCourseCookTime - itemTargetCookSeconds`; `EXPO` cannot bump `DELIVERED_BUMPED` until child station lines are ready (unless Expo override). |
| **`HspKitchenSafetyLog`** | `checkType` (`WALK_IN_COOLER`, `FREEZER`, `HOT_HOLDING`, `COOK_INTERNAL_TEMP`, `SANITIZER_PPM`, `OPENING_LINE_CHECK`), `equipmentOrItemName` (String), `measuredValue` (`Decimal128`), `unit` (`CELSIUS`, `FAHRENHEIT`, `PPM`), `minSafeBound` (`Decimal128`), `maxSafeBound` (`Decimal128`), `complianceState` (`PASS`, `OUT_OF_RANGE_ACTION_REQUIRED`, `RESOLVED`), `correctiveActionNote` (String) | `outletId` -> `HspRestaurantOutlet.id`, `loggedByEmployeeId` -> `HrEmployee.id`, `workOrderId` -> `MfgMaintenanceWorkOrder.id` (optional) | Append-only food-safety audit record; `measuredValue` outside `[minSafeBound, maxSafeBound]` forces `OUT_OF_RANGE_ACTION_REQUIRED` and triggers Home `WorkItem`. |
| **`HspTipPoolAllocation`** | `businessDate` (Date), `shiftCode` (`AM`, `PM`, `LATE`), `grossCreditTips` (`Decimal128`), `declaredCashTips` (`Decimal128`), `poolRuleSummary` (String), `distributions` (JSON array of `{ employeeId, roleName, hoursWorked: Decimal128, poolPoints: Decimal128, allocatedTipAmount: Decimal128 }`), `status` (`DRAFT`, `PENDING_APPROVAL`, `APPROVED_EXPORTED`) | `outletId` -> `HspRestaurantOutlet.id`, `payrollRunId` -> `HrPayrollRun.id` (optional), `glJournalEntryId` -> `FinJournalEntry.id` | Sum of `distributions[].allocatedTipAmount` must equal `grossCreditTips + declaredCashTips` to `0.01` `Decimal128` precision; immutable once `APPROVED_EXPORTED`. |

---

## 5. Core End-to-End User Journeys

### Journey 1: Full-Service Coursing & Synchronized Multi-Station KDS Execution
1. When the host seats a party of 4 at Table `12` in `#171` (noting a severe `SHELLFISH` allergy), `#170` receives `hsp.table.party_seated` and opens `HspDiningCheck` `#CHK-4092` displaying a high-visibility red `SHELLFISH ALLERGY` banner.
2. The server punches in Course 1 (Calamari, Burrata) and Course 2 (Seat 1: `14-min` Ribeye Med-Rare on `GRILL`; Seat 2: `4-min` Crispy Truffle Fries + Fish & Chips on `FRY`) and taps **Send & Fire Course 1 (Hold Course 2)**.
3. Once Course 1 is cleared, the server taps **Fire Course 2**: `GRILL` immediately transitions the Ribeye ticket to `PREPARING`, while `FRY` holds the `4-min` Fish & Chips in `WAITING_TO_FIRE` for 10 minutes before auto-illuminating—so both dishes arrive hot simultaneously at `MASTER_EXPO`, where the Expeditor verifies the allergy sticker and taps **Bump to Runner**.

### Journey 2: Chef Instant `86` Countdown on KDS Blocking Omnichannel Sales
1. During Friday dinner rush, the Sous-Chef notices only `3` portions of Halibut remain and sets `HspMenuItem` Halibut to `COUNTDOWN (3)` from `#/eighty-six-board`.
2. Two dine-in seats and one DoorDash order claim the final 3 portions, atomically decrementing `remainingPortions` to `0` and flipping `availabilityStatus` to `EIGHTY_SIXED`.
3. Within 2 seconds, Halibut is grayed out on server handhelds, tabletop QR menus (`ComSite`), and 3rd-party delivery feeds—preventing awkward table-side apologies and delivery cancellations.

### Journey 3: Split Check by Seat & Hotel Guest Charge-to-Room Settlement
1. At the end of dinner on `#CHK-4092` (`\$248.60`), Seat 1 & Seat 2 ask to split their items onto a personal card, while Seat 3 & Seat 4 are staying in Room `514` at the attached hotel (`#169`).
2. Inside `#/check-detail`, the server splits `#CHK-4092` by seat with exact `Decimal128` tax allocation: Sub-check A (`\$118.20`) settles via `pos` (`ComPosTransaction`) + `payments` (`FinPaymentIntent`), while Sub-check B (`\$130.40` + `\$26.00` tip) verifies Room `514` via `#169` and invokes `hsp.pms.postRoomChargeFromPos`—closing both checks cleanly.

### Journey 4: Post-Fire Comp Governance & Critical HACCP Cooler Alert via Home `WorkItem`s
1. A line cook accidentally overcooks a `\$58.00` Wagyu Strip; the server submits a post-fire void (`MADE_WAS_WASTED`) + remake in `safety-log-drawer`. Because `\$58.00` exceeds the `\$25.00` server threshold, `#170` fires the remake immediately to protect guest hospitality while routing a Rapider Home `WorkItem` to the Floor Manager for comp sign-off and emitting `hsp.restaurant.waste_logged` to `#175` Food Costing.
2. During closing line checks (`#/haccp-safety`), a cook logs Walk-In Cooler #2 at `9.4°C` (above the `4.0°C` `maxSafeBound`). The drawer enforces a corrective action note ("Moved dairy/proteins to Cooler #1"), marks `OUT_OF_RANGE_ACTION_REQUIRED`, creates a high-priority Home `WorkItem` for the GM, and spawns an urgent `MfgMaintenanceWorkOrder` in `maintenance`.

### Journey 5: Shift Tip-Pool Reconciliation & List-to-Detail Filter Restoration
1. At `01:00` shift close (`#/tip-pools-zread`), the Manager computes `HspTipPoolAllocation` combining `\$1,840.50` credit tips (`FinPaymentIntent`) and `\$215.00` declared cash tips across Servers (70%), Bartenders (18%), and Bussers/Runners (12%) weighted by `HrAttendancePunch` worked hours, approves the `Decimal128`-exact ledger, and exports to `payroll` + `acc` (`FinJournalEntry`).
2. In `#/dining-checks`, the Manager searches `Room` and selects pill `Status: "CHARGED_TO_ROOM"`, clicks `#CHK-4092B` to inspect `#/check-detail?id=...`, and clicks **Back to Checks**—preserving `#activeFilterTagsBar` chips without reload.

---

## 6. Consolidated Feature Priorities & Work Packages

### `P0` Foundation Work Packages (Mandatory MVP Launch)
- **WP-P0-1: Daypart Menus, Nested Modifiers, Allergens & Live `86` (`RKO-001`, `RKO-002`, `RKO-003`):** `HspRestaurantOutlet`, `HspRestaurantMenu`, `HspMenuItem`, `HspModifierGroup`, `#/menus-modifiers`, and instant `#/eighty-six-board` countdowns.
- **WP-P0-2: Dining Checks, Multi-Course Firing & Split-Check POS Handoff (`RKO-006`, `RKO-007`, `RKO-008`):** `#/dining-checks`, `#/check-detail`, seat/course matrix, exact `Decimal128` split checks, and `ComPosTransaction` / `FinPaymentIntent` settlement.
- **WP-P0-3: Multi-Station KDS, Synchronized Cook Pacing & All-Day Counts (`RKO-011`, `RKO-012`, `RKO-013`):** `<rapider-kanban>` `#/kds-board` with Prep vs. Expo views, delayed cook-time firing, *All-Day* aggregated item panel, color SLA timers, and Bump/Recall.
- **WP-P0-4: Tablet-Free Delivery Ingestion, Void Governance & PMIX Events (`RKO-016`, `RKO-019`, `RKO-020`):** `#/delivery-hub` webhook normalization, pre-fire vs. post-fire waste tracking (`MADE_WAS_WASTED`) with Home `WorkItem` comp approvals, and real-time `PMIX` event emission to `#175` + `inventory`.

### `P1` Scale & Enterprise Work Packages
- **WP-P1-1: Brand Menu Inheritance, Combos, Tabletop QR & Hotel Room Charge (`RKO-004`, `RKO-005`, `RKO-009`, `RKO-010`):** Multi-location LTO publishing, prix-fixe/combo bundles, QR check append, and `#169` PMS room-charge posting.
- **WP-P1-2: Station Failover, Pickup Screens & Dynamic Delivery Throttling (`RKO-014`, `RKO-015`, `RKO-017`, `RKO-018`):** Closed-station fallback routing, counter pickup board + SMS ready alerts, backlog-driven quote extensions, and Expo tamper-seal checklists.
- **WP-P1-3: HACCP Food Safety, Tip Pools, Z-Read GL & Speed Analytics (`RKO-021`, `RKO-022`, `RKO-023`, `RKO-024`):** `#/haccp-safety` logs + `MfgMaintenanceWorkOrder` escalation, `#/tip-pools-zread` weighted by `HrAttendancePunch` -> `payroll`/`FinJournalEntry`, and `#/voids-speed-audit`.

### `P2` Adjacent & Grounded AI Work Packages
- **WP-P2-1: Grounded AI Morning Prep Sheets & Bottleneck Advisor (`RKO-025`, `RKO-026`):** Prep-par recommendations grounded in `#171` booked covers + historical `PMIX`, and station bottleneck diagnosis in `projectChannelMessage`.
- **WP-P2-2: Allergen-Safe Pairing Prompts & Loss-Prevention Anomaly Alerts (`RKO-027`, `RKO-028`):** Server upsell hints and suspicious post-print void/cash-comp pattern detection routed via Home `WorkItem`s.

---

## 7. Roles, Permissions & Field-Level Governance

| Role | Permitted Actions | Restricted / Field-Level Boundaries |
| :--- | :--- | :--- |
| **Server / Bartender** | Open/edit assigned `HspDiningCheck`s; fire courses; split checks; cancel unfired (`NOT_MADE`) draft items; initiate POS or Hotel Room-Charge payment; view own shift tips. | Cannot approve post-fire voids or comps above threshold (e.g., `\$25`); cannot alter menu prices; cannot view other employees' payroll tip payouts. |
| **Line Cook / Expeditor (Chef)** | View & bump `HspKitchenTicket`s on Prep/Expo KDS; recall bumped tickets; set `COUNTDOWN` or `EIGHTY_SIXED` on `HspMenuItem`; log `HspKitchenSafetyLog` temperatures. | Cannot settle payments, issue cash refunds, edit `HspTipPoolAllocation`, or delete historical safety logs. |
| **Floor Manager / Sous-Chef** | Approve post-fire void/comp Home `WorkItem`s; toggle `HspKitchenStation` fallback routing; adjust delivery `throttleMode`; resolve HACCP corrective actions; run shift Z-reads. | Cannot retroactively mutate `APPROVED_EXPORTED` tip pools or closed `FinJournalEntry` postings. |
| **Restaurant GM / F&B Director** | Publish brand/outlet `HspRestaurantMenu`s; configure tip-pool formulas, comp thresholds, tax mappings, and 3rd-party delivery webhooks; export `HspTipPoolAllocation` to `payroll`. | All menu price changes, void approvals, and tip-pool formula edits are recorded in immutable audit logs. |

---

## 8. Technical APIs, Guarded Commands, Events & `requiredWorkflows`

### 8.1 Guarded Domain Commands
Every mutating command enforces `{ idempotencyKey, correlationId, expectedVersion }`:
- `hsp.restaurant.fireCourseToKitchen` — Validates all forced modifier selections (`minSelections..maxSelections`), decrements `COUNTDOWN` portions atomically (rejecting if `0`), computes synchronized `scheduledFireAt` per item's `targetCookSeconds`, and creates station `HspKitchenTicket`s.
- `hsp.restaurant.bumpOrRecallTicket` — Transitions station `HspKitchenTicket` (`PREPARING` -> `PLATING_EXPO` -> `DELIVERED_BUMPED` or `RECALLED`), recording exact `actualCookSeconds`.
- `hsp.restaurant.eightySixMenuItem` — Atomically updates `availabilityStatus` (`EIGHTY_SIXED` or `COUNTDOWN`) and triggers omnichannel menu availability broadcast.
- `hsp.restaurant.splitDiningCheck` — Splits `HspDiningCheck` by seat, item, or `1/N` fraction using deterministic `Decimal128` penny allocation so `sum(children) == parent`.
- `hsp.restaurant.voidOrCompCheckItem` — Records `MADE_WAS_WASTED` vs. `NOT_MADE` reason code; executes immediately within role cap or creates a Rapider Home `WorkItem` for Manager approval.
- `hsp.restaurant.logSafetyCheck` — Appends immutable `HspKitchenSafetyLog`; if out of `[minSafeBound, maxSafeBound]`, spawns Home `WorkItem` and optional `MfgMaintenanceWorkOrder`.
- `hsp.restaurant.approveTipPoolAndZRead` — Validates `Decimal128` tip distribution equality, locks shift checks, emits `FinJournalEntry` to `acc`, and sends tip payouts to `payroll`.

### 8.2 Published & Consumed Kafka Domain Events
- **Published:** `hsp.restaurant.course_fired`, `hsp.restaurant.ticket_bumped`, `hsp.restaurant.item_eighty_sixed`, `hsp.restaurant.check_settled`, `hsp.restaurant.pmix_recorded`, `hsp.restaurant.waste_logged`, `hsp.restaurant.safety_excursion_detected`.
- **Consumed:** `hsp.table.party_seated` (from `#171`), `com.pos.transaction_completed` (from `pos`), `fin.payment_intent.succeeded` (from `payments`), `hsp.recipe.margin_alert_raised` (from `#175`).

### 8.3 `requiredWorkflows` (Declared in `app.manifest.json`)
1. `wf-hsp-kds-delayed-course-awakener` — Evaluates `WAITING_TO_FIRE` tickets every 10 seconds to illuminate shorter-cook stations at exact `scheduledFireAt` (`RKO-012`).
2. `wf-hsp-omnichannel-86-and-throttle-sync` — Broadcasts `EIGHTY_SIXED` state and dynamic `throttleMode` quote minutes to `ComSite` QR/online ordering and 3rd-party delivery webhooks (`RKO-003`, `RKO-017`).
3. `wf-hsp-void-and-haccp-escalation` — Routes high-value post-fire comps/voids and critical cooler temperature excursions to Rapider Home `WorkItem`s (`RKO-019`, `RKO-021`).
4. `wf-hsp-nightly-zread-pmix-tip-export` — Consolidates end-of-day `PMIX` for `#175`, posts outlet `FinJournalEntry` to `acc`, and stages `HspTipPoolAllocation` for `payroll` (`RKO-020`, `RKO-022`, `RKO-023`).

### 8.4 Grounded Rapider AI Guardrails
- AI Prep-Sheet Recommender, Kitchen Bottleneck Advisor, and Loss-Prevention Anomaly Detector cite exact `HspDiningCheck`, `HspKitchenTicket`, `HspMenuItem`, and `#171` `HspDiningReservation` IDs within user RBAC permissions.
- AI **never** silently `86`s menu items, pauses 3rd-party delivery marketplaces, approves post-fire comps, or alters `HspTipPoolAllocation` shares without explicit human confirmation.

---

## 9. Security, Privacy, Compliance & Non-Functional Requirements

- **Food Safety & Allergen Liability Governance (FDA Food Code / EU 1169/2011):** Mandatory 14-major-allergen structured tags propagate unbroken from `HspMenuItem` / `HspModifierGroup` -> `HspDiningCheck` -> Prep & Expo `HspKitchenTicket` headers; `HspKitchenSafetyLog` records are append-only and retained for >= 3 years for health-department inspections.
- **Labor & Tip Wage Compliance (FLSA / Regional Tip-Pooling Laws):** `HspTipPoolAllocation` enforces configurable role eligibility rules (preventing salaried managers/owners from drawing from employee tip pools) with full calculation lineage tied to `HrAttendancePunch`.
- **PCI-DSS & Guest PII Minimization:** Zero cardholder data stored in `Hsp*`; delivery customer phone numbers (`<rapider-phone-input>`) are masked after order completion according to marketplace data-retention terms.
- **Kitchen Hardware Resilience & Accessibility:** High-contrast dark/light KDS cards (`>= 44x44px` touch targets for gloved/wet hands), WCAG 2.2 AA compliance, and responsive layouts across `1440px` wall-mounted Expo monitors, `768px` POS/Prep tablets, and `390px` server handhelds.

---

## 10. Deterministic Acceptance Criteria

1. **Sidebar Minimum-3-Items Compliance:** `app.manifest.json` organizes visible routes into 3 sections (`Overview`, `Kitchen & Service`, `Governance`) with 3 visible items each (`displayOnMenu: true`); detail and drawer routes set `displayOnMenu: false`.
2. **Forced Modifier & Allergen Validation:** Firing a check line whose `FORCED_EXACT` modifier group lacks a required selection (e.g., Steak Temp) blocks firing with inline field validation; allergy banners on `HspDiningCheck` render visibly on all spawned `HspKitchenTicket`s.
3. **Atomic Countdown-to-`86` Guard:** Firing 2 concurrent orders for a `HspMenuItem` with `remainingPortions == 1` succeeds for the first (transitioning `availabilityStatus` to `EIGHTY_SIXED`) and deterministically rejects the second with an actionable out-of-stock prompt.
4. **Synchronized Multi-Station Delayed Firing:** Firing a course containing a `840s` (`14m`) Grill item and a `240s` (`4m`) Fry item sets Grill `status = PREPARING` immediately and Fry `status = WAITING_TO_FIRE` with `scheduledFireAt == firedAt + 600s`.
5. **Station Fallback Continuity:** Marking `SAUTE` `isOnline = false` automatically routes newly fired `SAUTE` items to its configured `fallbackStationId` (`GRILL`) with zero dropped ticket lines.
6. **Exact `Decimal128` Split-Check Invariance:** Splitting a `\$100.00` check `3` ways (`1/3`) produces sub-checks of `\$33.34`, `\$33.33`, and `\$33.33` using `Decimal128` so `sum(subChecks) == \$100.00` with zero floating-point drift.
7. **Post-Fire Void & Waste Segregation:** Post-fire voids (`MADE_WAS_WASTED`) exceeding the server threshold generate a Rapider Home `WorkItem` and emit `hsp.restaurant.waste_logged` to `#175` Food Costing.
8. **Critical HACCP Excursion Gate:** Logging a walk-in cooler reading above `maxSafeBound` requires a non-empty `correctiveActionNote`, sets `OUT_OF_RANGE_ACTION_REQUIRED`, and creates a Rapider Home `WorkItem`.
9. **Tip-Pool `Decimal128` Conservation & Manager Exclusion:** `approveTipPoolAndZRead` rejects any distribution containing an ineligible salaried manager role or where `sum(allocatedTipAmount) != grossCreditTips + declaredCashTips`.
10. **Custom Elements Adoption:** Delivery/takeout phone fields use `<rapider-phone-input>` and `#/kds-board` renders ticket states using `<rapider-kanban>`.
11. **SWR Clean Query & Optimistic UI Standard:** All initial loads use `findSWR` / `countSWR` without `isDeleted` API query filters, optimistically update local arrays + clear SWR cache on drawer save/delete, and reset button states inside `finally`.
12. **Table Action & Click-Through Navigation Standard:** Data tables omit standalone `View` buttons; clicking `#CHK-...` navigates to `#/check-detail?id=...` without `<base href>` 404 diversion, and `Back` restores `#/dining-checks` filters.
13. **Search, `#activeFilterTagsBar` & `Clear all`:** Filtering checks, menus, or safety logs renders HTML-escaped chips in `#activeFilterTagsBar` with `✕` chip dismissal and `Clear all` reset.
14. **Theme & Button Contrast Compliance:** All 13 routes pass `validate_theme` across light and dark modes (including KDS dark mode) with `#ffffff !important` text on primary and danger buttons and zero `window.alert`/`confirm`/`prompt` calls.

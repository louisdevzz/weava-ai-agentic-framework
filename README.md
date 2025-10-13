# 🧠 Weava AI Agentic Framework

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=28&duration=2800&pause=1200&color=7353FF&center=true&vCenter=true&width=800&lines=Weava+AI+Agentic+Framework;Distributed+Neural+Fabric+for+Autonomous+Agents" alt="Weava AI Agentic Framework Banner" />
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-4C1.svg" alt="License" /></a>
  <img src="https://img.shields.io/badge/status-Incubating-orange.svg" alt="Project status" />
  <img src="https://img.shields.io/badge/language-Python%203.11+-3776AB.svg" alt="Primary language" />
</p>

## 🔖 Mục lục
- [Tổng quan](#-tổng-quan)
- [Tầm nhìn](#-tầm-nhìn)
- [Năng lực cốt lõi](#-năng-lực-cốt-lõi)
- [Kiến trúc tổng quan](#-kiến-trúc-tổng-quan)
- [Nguyên lý vận hành](#-nguyên-lý-vận-hành)
- [Thành phần & công nghệ](#-thành-phần--công-nghệ)
- [Quickstart](#-quickstart)
- [Ứng dụng mẫu](#-ứng-dụng-mẫu)
- [Lộ trình](#-lộ-trình)
- [Đóng góp](#-đóng-góp)
- [Giấy phép](#-giấy-phép)

## 📋 Tổng quan
Weava AI Agentic Framework là hạ tầng phân tán dành cho autonomous AI agents, hỗ trợ nhà phát triển tạo, đăng ký, khám phá và kết nối các agent thông minh trên một "distributed neural fabric". Framework tập trung vào tính mô-đun, khả năng mở rộng theo chiều ngang và giao tiếp tự động giữa các agent.

## 🎯 Tầm nhìn
- Kiến tạo **Agentic Web** nơi mỗi agent sở hữu danh tính riêng thông qua `AgentCard`.
- Cho phép agent khám phá, hợp tác và phối hợp trên mesh mà không cần cấu hình thủ công.
- Chuẩn hoá tương tác thông qua giao thức tương thích **Model Context Protocol (MCP)**.
- Xây dựng cơ chế bảo mật, giám sát và mở rộng ngay từ kiến trúc gốc.

## ⚡ Năng lực cốt lõi
- 🐍 **Agent SDK (Python)**: tạo agent mới, khai báo capability, ký định danh và giao tiếp qua mesh.
- 📋 **Agent Registry Service**: đăng ký và khám phá agent bằng metadata, năng lực và embedding kỹ năng.
- 🌐 **Messaging Mesh**: lớp kết nối agent-to-agent dựa trên NATS/JetStream bảo đảm độ trễ thấp.
- 🔍 **Discovery Engine**: tìm kiếm agent bằng ngôn ngữ tự nhiên hoặc vector hoá kỹ năng.
- 🤝 **Handshake & Session Layer**: thiết lập phiên, xác thực khóa công khai và quản lý vòng đời hội thoại.
- 🔧 **MCP Tool Adapters**: cung cấp adapter tới HTTP API, browser và dịch vụ web bên ngoài.
- 📊 **Audit & Governance**: giám sát hành vi, ghi sổ append-only và thực thi chính sách truy cập.

## 🏗️ Kiến trúc tổng quan
```
┌───────────────────────────────────────────────────────────┐
│                   🧠 Weava AI Framework                   │
├───────────────────────────────────────────────────────────┤
│ 👤 User / Developer                                      │
│    → Tạo agent bằng SDK, định nghĩa capability & goal     │
│                                                           │
│ 📋 Registry Layer                                        │
│    → Lưu & tìm AgentCard, search theo ngữ nghĩa           │
│                                                           │
│ 🌐 Mesh Communication                                    │
│    → Agent ↔ Agent giao tiếp qua NATS Pub/Sub             │
│                                                           │
│ 🤝 Session Layer                                         │
│    → Handshake, tạo phiên, quản lý luồng hội thoại        │
│                                                           │
│ 🔧 Tool Layer (MCP)                                      │
│    → Adapter cho HTTP / Browser / Custom Tools            │
│                                                           │
│ 📊 Audit & Governance                                    │
│    → Theo dõi, log, bảo mật, kiểm tra chữ ký & hành vi    │
└───────────────────────────────────────────────────────────┘
```

## ⚙️ Nguyên lý vận hành
```
┌────────────────────────────────────────────────────────┐
│                🧠 Weava AI Agentic Framework            │
├────────────────────────────────────────────────────────┤
│ 🎯 1. User Intent Layer (Goal Understanding)            │
│   → Nhận mục tiêu người dùng, sinh "Intent Graph"      │
│                                                        │
│ 🗺️ 2. Context & Skill Mapping Layer                     │
│   → Dùng Demand Skill Vector Mapper                     │
│   → Gán mục tiêu vào vector kỹ năng agent hiểu được     │
│                                                        │
│ 🚦 3. Distributed Routing Layer                          │
│   → Real-Time Task Router tìm Agent phù hợp             │
│                                                        │
│ 🤝 4. Collaboration Layer                                │
│   → Giao thức Agent-to-Agent (A2A)                      │
│                                                        │
│ 🔗 5. Resource Integration Layer                         │
│   → Dựa trên MCP để truy cập API, DB, tools             │
│                                                        │
│ 💰 6. Economic/Trust Layer                               │
│   → Cross-Agent Ledger theo dõi nguồn lực               │
│                                                        │
│ 📊 7. Monitoring & Governance Layer                      │
│   → Quản lý trạng thái, audit, bảo mật                  │
└────────────────────────────────────────────────────────┘
```

## 🛠️ Thành phần & công nghệ
| Thành phần            | Công nghệ chính             | Ghi chú |
|-----------------------|-----------------------------|---------|
| 🌐 Registry API       | FastAPI · PostgreSQL        | Lưu trữ metadata & AgentCard |
| 📡 Messaging          | NATS · JetStream            | Pub/Sub và event streaming |
| 🐍 Agent SDK          | Python 3.11+                | Định nghĩa agent, capability, policy |
| 🔍 Vector Search      | FAISS                       | Semantic discovery & ranking |
| 🔧 Tool Adapters      | MCP-compatible wrappers     | HTTP, Browser, dịch vụ tùy chỉnh |
| 📝 Logging            | JSONL · Hash chain          | Tamper-evident audit trail |
| 📊 Dashboard          | Next.js · FastAPI templates | Quan sát hệ thống, live ops |

## 🚀 Quickstart
1. **Chuẩn bị môi trường**
   - Python 3.11 trở lên, Docker (tùy chọn cho mesh services).
   - Tạo virtualenv: `python -m venv .venv && source .venv/bin/activate`.
2. **Cài đặt dependencies** *(đang được đóng gói)*
   - Sử dụng `pip install -r requirements.txt` khi manifest được công bố.
   - Các dịch vụ mesh (NATS, PostgreSQL) có docker-compose sample.
3. **Tạo agent đầu tiên**
   - `from weava_sdk import Agent` → khai báo capability, skill set và đăng ký với Registry.
4. **Khởi chạy mesh**
   - Khởi động NATS/JetStream, Registry API và Discovery Engine.
   - Agent kết nối qua SDK, handshake, và hiển thị trên dashboard real-time.

> ℹ️ Các hướng dẫn chi tiết sẽ được bổ sung khi release builder toolchain.

## 🤖 Ứng dụng mẫu
- 📊 Liên minh agent phân tích dữ liệu và đồng bộ insight.
- 🔬 Mạng nghiên cứu tự động tìm cộng sự và chia sẻ kết quả.
- ⚙️ Pipeline multi-agent: crawl → summarize → report → verify với audit ledger.
- 🤖 Autonomous assistant phối hợp với agent hệ sinh thái khác qua MCP.

## 🗺️ Lộ trình
- ✅ **Core SDK**, Registry API, Messaging Mesh, Handshake Protocol, Tool Adapters.
- 🧩 **Dashboard** đang phát triển cho telemetry & control plane.
- 🔜 **Semantic Discovery v1.5** với hybrid search và ranking.
- 🔜 **Trust Graph & Governance v2** cho policy-based routing.
- 🌍 **Tầm nhìn dài hạn**: Cognitive Agentic Infrastructure cùng adaptive ontology, RL routing và cognitive governance fabric.

## 🤝 Đóng góp
- Hãy mở issue khi cần tính năng mới, bugfix hoặc đề xuất tích hợp.
- Định dạng commit theo Conventional Commits để dễ dàng tự động hóa.
- Đóng góp code vui lòng kèm test, linters và cập nhật cấu hình liên quan.

## 📄 Giấy phép
Dự án được phân phối theo giấy phép [MIT](LICENSE).

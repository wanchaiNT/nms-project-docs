# NT Network Operation - Project Blueprint

Version: 0.1.0  
Status: Architecture Phase  
Owner: wanchaiNT  
Project Type: Enterprise Network Operation Platform

---

## 1. Project Overview

NT Network Operation คือระบบ Enterprise Infrastructure Monitoring Platform สำหรับตรวจสอบ ดูแล และบริหารจัดการอุปกรณ์เครือข่ายและอุปกรณ์โครงสร้างพื้นฐานของลูกค้าหลายไซต์

ระบบถูกออกแบบให้ใช้ได้กับงาน NOC, ช่างภาคสนาม, ผู้ดูแลระบบ และลูกค้าองค์กร โดยรองรับการตรวจสอบสถานะผ่าน Ping, SNMP, API และระบบแจ้งเตือนแบบ Real-time

---

## 2. Project Goals

เป้าหมายหลักของระบบคือ

1. ตรวจสอบสถานะ Site และ Device แบบรวมศูนย์
2. ลดเวลาการตรวจพบปัญหา
3. แจ้งเตือนช่างตาม Site ที่รับผิดชอบ
4. ให้ลูกค้าดูสถานะเฉพาะ Site ของตัวเอง
5. เก็บประวัติ Alarm, Downtime และ SLA
6. รองรับการวิเคราะห์ปัญหาด้วย AI ในอนาคต
7. รองรับการขยายเป็นระบบ Enterprise และ Multi-Tenant

---

## 3. User Roles

### 3.1 Admin

Admin สามารถจัดการระบบทั้งหมด เช่น User, Site, Device, Notification, Report และ Settings

### 3.2 Technician

Technician ใช้ตรวจสอบสถานะอุปกรณ์ รับ Alarm และบันทึกการแก้ไขปัญหา

### 3.3 Customer

Customer ดูข้อมูลเฉพาะ Site ของตัวเอง ไม่สามารถแก้ไขข้อมูลหลักได้

### 3.4 Viewer

Viewer ดูข้อมูลได้อย่างเดียว ใช้สำหรับผู้บริหารหรือจอ NOC TV

---

## 4. Core Modules

ระบบประกอบด้วย Module หลักดังนี้

1. Authentication
2. Dashboard
3. Map
4. Site Management
5. Device Management
6. Alarm Management
7. Notification Center
8. Report & Export
9. Settings
10. User & Role Management
11. Monitoring Engine
12. Ping Engine
13. SNMP Engine
14. Device Template
15. Device Profile
16. Inventory
17. Maintenance Window
18. SLA Report
19. Topology
20. AI Root Cause Analysis

---

## 5. System Architecture

สถาปัตยกรรมหลักของระบบ:

```text
User Browser
    |
    v
Next.js Frontend
    |
    v
Backend API
    |
    +--> PostgreSQL
    +--> Redis
    +--> Monitoring Engine
    +--> Notification Engine
    +--> AI Analysis Service
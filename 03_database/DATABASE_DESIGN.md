# NT Network Operation - Database Design

Version: 0.1.0  
Status: Draft

---

## 1. Database Goals

Database ต้องรองรับระบบ Enterprise Network Operation Platform ที่มีหลายองค์กร หลายไซต์ หลายอุปกรณ์ หลายผู้ใช้งาน และข้อมูล Monitoring จำนวนมาก

---

## 2. Core Entities

### Organization

ใช้เก็บข้อมูลลูกค้าหรือหน่วยงาน

### User

ใช้เก็บบัญชีผู้ใช้งาน

### Role

ใช้กำหนดบทบาท เช่น Admin, Technician, Customer, Viewer

### Permission

ใช้กำหนดสิทธิ์แบบละเอียด

### Site

ใช้เก็บข้อมูลไซต์งาน

### Device

ใช้เก็บข้อมูลอุปกรณ์ เช่น Router, Switch, CCTV, NVR, UPS

### Device Profile

ใช้เก็บรูปแบบอุปกรณ์ตาม Vendor / Model

### Device Template

ใช้กำหนดค่า Monitoring มาตรฐาน เช่น OID, Ping, Interface, CPU, Memory

### Alarm

ใช้เก็บเหตุขัดข้องที่ยัง Active หรือปิดแล้ว

### Alarm Event

ใช้เก็บ Timeline ของ Alarm

### Notification Channel

ใช้เก็บช่องทางแจ้งเตือน เช่น Telegram, Email, LINE

### Maintenance Window

ใช้กำหนดช่วงเวลาซ่อมบำรุง

### SLA Record

ใช้เก็บข้อมูล Availability และ Downtime

### Audit Log

ใช้เก็บประวัติการกระทำของผู้ใช้

---

## 3. Initial Table List

```text
organizations
users
roles
permissions
role_permissions
user_roles
sites
devices
device_profiles
device_templates
alarms
alarm_events
notification_channels
notification_rules
maintenance_windows
sla_records
audit_logs
inventory_assets
config_backups
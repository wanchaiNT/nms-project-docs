# NT Network Operation - ER Diagram

Version: 0.1.0
Status: Draft

---

## 1. Purpose

เอกสารนี้ใช้อธิบายความสัมพันธ์หลักของฐานข้อมูลสำหรับระบบ NT Network Operation

เป้าหมายคือให้ทีมพัฒนาและ AI เข้าใจว่า Entity หลักของระบบเชื่อมโยงกันอย่างไร ก่อนเริ่มสร้าง Prisma Schema และ Database Migration

---

## 2. High-Level ER Diagram

```text
organizations
    |
    |--- users
    |--- sites
    |--- roles
    |--- notification_channels
    |--- audit_logs
    |
sites
    |
    |--- devices
    |--- maintenance_windows
    |--- sla_records
    |
devices
    |
    |--- alarms
    |--- inventory_assets
    |--- config_backups
    |
alarms
    |
    |--- alarm_events
```

---

## 3. RBAC Relationship

```text
users
    |
    |--- user_roles
            |
            |--- roles
                    |
                    |--- role_permissions
                            |
                            |--- permissions
```

---

## 4. Monitoring Relationship

```text
device_profiles
    |
    |--- devices

device_templates
    |
    |--- devices

devices
    |
    |--- alarms
    |--- config_backups
    |--- inventory_assets

alarms
    |
    |--- alarm_events
```

---

## 5. Notification Relationship

```text
organizations
    |
    |--- notification_channels
            |
            |--- notification_rules

sites
    |
    |--- notification_rules

devices
    |
    |--- notification_rules
```

---

## 6. Core Relationship Summary

| Parent Table          | Child Table        | Relationship                             |
| --------------------- | ------------------ | ---------------------------------------- |
| organizations         | users              | One organization has many users          |
| organizations         | sites              | One organization has many sites          |
| organizations         | roles              | One organization has many roles          |
| sites                 | devices            | One site has many devices                |
| devices               | alarms             | One device has many alarms               |
| alarms                | alarm_events       | One alarm has many events                |
| users                 | user_roles         | One user can have many roles             |
| roles                 | role_permissions   | One role can have many permissions       |
| device_profiles       | devices            | One profile can be used by many devices  |
| device_templates      | devices            | One template can be used by many devices |
| notification_channels | notification_rules | One channel can be used by many rules    |

---

## 7. Multi-Tenant Rule

ทุกตารางที่เป็นข้อมูลธุรกิจหลักต้องมี `organization_id` เพื่อแยกข้อมูลแต่ละองค์กรออกจากกัน

ตารางที่ควรมี `organization_id` ได้แก่:

```text
users
roles
sites
devices
alarms
notification_channels
notification_rules
maintenance_windows
sla_records
audit_logs
inventory_assets
config_backups
```

---

## 8. Next Step

ขั้นต่อไปคือการสร้าง Table Specification แบบละเอียด โดยกำหนด Field, Type, Relation, Index และ Constraint ของแต่ละตาราง

```
```

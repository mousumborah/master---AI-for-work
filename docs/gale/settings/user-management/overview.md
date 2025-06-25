# Users Management

The **Users Management** module is crucial for handling user-related activities within your organization. This module provides capabilities for the following:

- **Managing Users**: Add users to your account, assign a default user role, view user status, unlock a locked user, and delete one or more user from your account. [Learn more](../user-management/users.md){:target="_blank"}.
- **Managing Roles, and Permissions**: Assign and configure roles, set module-wise account/agent permissions, and manage user access efficiently. [Learn more](./role-management.md){:target="_blank"}.
- **Active Directory (AD) Synchronization (Sync)**: Integrate and synchronize your AD with organizational user data. [Learn more](./settings/active-directory.md){:target="_blank"}.
- **Configuring User Profile Fields**: Set visibility and editability rules for user profile fields specific to your domain. [Learn more](./settings/active-directory.md/#step-3-specify-user-attributes-and-configure-rules-for-selective-import-from-ad){:target="_blank"}.
- **Email Notifications**: Configure email notifications for users depending on whether they joined your account by invitation or through AD sync. [Learn more](./settings/active-directory.md/#sync-status-email-notifications){:target="_blank"}.

This [Users](./users.md){:target="_blank"} page provides detailed instructions and guidelines on various capabilities available within the **Users Management** module for administering user-related operations, such as the following:

- Role and permissions management for different modules. [Learn more](./role-management.md){:target="_blank"}.
- AD sync and user profile configuration. [Learn more](./settings/active-directory.md/#active-directory-configuring-automatic-user-data-synchronization){:target="_blank"}.

**Users Management** streamlines user administration and enhances operational efficiency. 

It also supports various administrative features influenced by the roles and permissions assigned at the account or agent level. This includes actions you can perform on both external and existing GALE users:

- **System Roles**: Predefined roles with default permissions for basic system functionality. [Learn more](./role-management.md/#manage-system-roles){:target="_blank"}.
- **Custom Roles**: User-defined roles tailored to specific needs with customized access definitions for module-wise permissions. [Learn more](./role-management.md/#manage-custom-roles){:target="_blank"}.

For example, a *Master Admin* role is assigned by default to the account owner. Similarly, an *Agent Admin* role is assigned to a user who creates an agent and has complete control over it.

**Users Management** operates on two distinct levels discussed [here](../settings-overview.md/#levels-of-users-management){:target="_blank"}.

Once you invite a user or import users data, you can change their roles, assign/unassign permissions, delete users. and do more using the [Roles Management](./role-management.md){:target="_blank"} and [Users](./users.md){:target="_blank"} features on the **Settings** console.

## Related Information

* **Settings Console** - [Learn more](../../settings-overview.md){:target="_blank"} about other GALE admin features.
* **Role Management** - [Learn more](../user-management/role-management.md){:target="_blank"} about managing default and custom roles in your account.
* **Monitoring: Audit Logs** - [Learn more](../monitoring/audit-logs.md){:target="_blank"} about tracking events and user activity in your account.
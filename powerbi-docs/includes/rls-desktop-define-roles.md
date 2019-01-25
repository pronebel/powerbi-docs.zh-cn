## <a name="define-roles-and-rules-in-power-bi-desktop"></a>在 Power BI Desktop 中定义角色和规则
你可以在 Power BI Desktop 中定义角色和规则。 发布到 Power BI 时，它还会发布角色定义。

若要定义安全角色，请执行以下步骤。

1. 将数据导入 Power BI Desktop 报表，或配置 DirectQuery 连接。
   
   > [!NOTE]
   > 不能在 Power BI Desktop 中为 Analysis Services 实时连接定义角色。 需要在 Analysis Services 模型中执行此操作。
   > 
   > 
1. 选择“建模”选项卡。
2. 选择“管理角色”。
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
4. 选择“创建”。
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
5. 为角色提供名称。 
6. 选择你想要应用 DAX 规则的表。
7. 输入 DAX 表达式。 此表达式应返回 true 或 false。 例如：[实体 ID] =“值”。
   
   > [!NOTE]
   > 可以在此表达式内使用 *username()*。 请注意，username() 在 Power BI Desktop 中采用“域\用户名”格式。 在 Power BI 服务和 Power BI 报表服务器中，采用用户的用户主体名称 (UPN) 格式。 或者，可以使用 userprincipalname()，它始终返回采用其用户主体名称格式 username@contoso.com 的用户。
   > 
   > 
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)
8. 创建 DAX 表达式后，你可以选择表达式框上方的“检查”以验证该表达式。
   
   ![](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
9. 选择**保存**。

无法在 Power BI Desktop 中将用户分配到角色。 在 Power BI 服务中分配用户。 通过使用 username() 或 userprincipalname() DAX 函数并配置好正确的关系，则可以启用 Power BI Desktop 中的动态安全。 


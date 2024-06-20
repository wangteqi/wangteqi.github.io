# Github中的配置

## 令牌创建

在Github上[创建令牌](https://github.com/settings/tokens/new)，点击 ==Generate new token==

![Github_1](./assets/Github_1.png)

相关选项

- Note: custom-site
- Expiration: No expiration
- Select scopes: repo, workflow, repo_hook

![Github_2](./assets/Github_2.png)

## 仓库创建

1. 在Github上[创建仓库](https://github.com/new)，点击 ==Create repository==

	![Github_3](./assets/Github_3.png)

2. 随后在[Action设置](https://github.com/wangteqi/wangteqi.github.io/settings/actions)中，调整 ==Workflow permission==

	![Github_4](./assets/Github_4.png)

3. 最后部署完之后，在[Page设置](https://github.com/wangteqi/wangteqi.github.io/settings/pages)中，把Branch调整到 ==gh-page== 分支

	![Github_5](./assets/Github_5.png)
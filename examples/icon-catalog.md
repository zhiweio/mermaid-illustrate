## Icon Catalog — 图标速查目录

本文件是所有 Mermaid 图表演示中可用的图标速查目录。基于 [Iconify](https://iconify.design/) 统一图标体系，精选 6 个 icon set 实现技术绘图全覆盖。

### Icon Set 速览

| Icon Set | 前缀 | 数量 | Palette | 定位 | 何时使用 |
|----------|------|------|---------|------|---------|
| **logos** | `logos` | 1,861 | ✓ | 产品/云服务 Logo | 云厂商、SaaS、开源项目 Logo |
| **devicon** | `devicon` | 1,036 | ✓ | 编程语言/工具/框架 | 技术栈图标，覆盖最广 |
| **gcp** | `gcp` | 214 | ✓ | Google Cloud 服务图标 | Google Cloud 各服务专用图标 |
| **vscode-icons** | `vscode-icons` | 1,513 | ✓ | 文件类型图标 | 文件/技术栈的 file-type 图标，命名规范 |
| **codicon** | `codicon` | 602 | ✗ | IDE/开发操作概念 | Git、终端、调试、文件操作 |
| **skill-icons** | `skill-icons` | 400 | ✓ | 编程技能图标 | 需 light/dark 主题变体时 |

### 图标查找决策树

绘制图表时，按以下优先级选择 icon set：

```
需要云服务/产品 Logo？
├── Google Cloud 服务图标？ → gcp（最全，214 个服务专用图标）
├── 其他云服务/产品 → logos（首选）或 devicon
└── 需要编程语言/框架/工具？
    ├── 需要文件类型图标（file-type-python、file-type-docker）？ → vscode-icons（命名规范，1,513 个）
    ├── 其他技术栈 → devicon（首选）或 skill-icons
    └── 需要 IDE/开发操作概念（Git、Terminal、Debug）？
        ├── 是 → codicon
        └── 不确定 → 搜索: https://api.iconify.design/search?query={keyword}&prefixes=logos,devicon,gcp,vscode-icons,codicon,skill-icons

🚫 **严禁 Emoji**: 所有图表中禁止使用 emoji 表情符号。始终使用本目录中的图标或语义着色来传达含义。
```

### 图标使用语法（按注册状态选择）

**核心决策规则**：根据渲染环境是否已注册图标包，选择对应语法。**同一张图中不要混用两种语法。**

**已注册图标包** → 使用 icon-pack 语法（推荐）：
```
%% flowchart
NodeName@{ icon: "logos:aws-ec2", form: "square", label: "EC2", pos: "b", h: 48 }

%% architecture-beta
service ec2(logos:aws-ec2)[EC2]
```

**未注册图标包** → 使用远程 URL 兜底（兼容所有环境）：
```
NodeName@{ img: "https://api.iconify.design/logos/aws-ec2.svg", label: "EC2", pos: "b", h: 48, constraint: "on" }
```

**API URL 模式**（远程兜底用）：
```
https://api.iconify.design/{prefix}/{icon-name}.svg
```

> ⚠️ **防变形铁律**：只设 `h`，开 `constraint: "on"`，绝不同时设 `w` 和 `h`。

---

## 1. 云服务 (Cloud Providers)

### 1.1 AWS

| 服务 | icon-pack 引用 | SVG URL | 宽高比 |
|------|---------------|---------|--------|
| AWS (通用) | `logos:aws` | `https://api.iconify.design/logos/aws.svg` | — |
| API Gateway | `logos:aws-api-gateway` | `https://api.iconify.design/logos/aws-api-gateway.svg` | 1:1 |
| AppFlow | `logos:aws-appflow` | `https://api.iconify.design/logos/aws-appflow.svg` | 1:1 |
| App Mesh | `logos:aws-app-mesh` | `https://api.iconify.design/logos/aws-app-mesh.svg` | 1:1 |
| AppSync | `logos:aws-appsync` | `https://api.iconify.design/logos/aws-appsync.svg` | 1:1 |
| Athena | `logos:aws-athena` | `https://api.iconify.design/logos/aws-athena.svg` | 1:1 |
| Aurora | `logos:aws-aurora` | `https://api.iconify.design/logos/aws-aurora.svg` | 1:1 |
| Backup | `logos:aws-backup` | `https://api.iconify.design/logos/aws-backup.svg` | 1:1 |
| Batch | `logos:aws-batch` | `https://api.iconify.design/logos/aws-batch.svg` | 1:1 |
| Certificate Manager | `logos:aws-certificate-manager` | `https://api.iconify.design/logos/aws-certificate-manager.svg` | 1:1 |
| CloudFormation | `logos:aws-cloudformation` | `https://api.iconify.design/logos/aws-cloudformation.svg` | 1:1 |
| CloudFront | `logos:aws-cloudfront` | `https://api.iconify.design/logos/aws-cloudfront.svg` | 1:1 |
| CloudSearch | `logos:aws-cloudsearch` | `https://api.iconify.design/logos/aws-cloudsearch.svg` | 1:1 |
| CloudTrail | `logos:aws-cloudtrail` | `https://api.iconify.design/logos/aws-cloudtrail.svg` | 1:1 |
| CloudWatch | `logos:aws-cloudwatch` | `https://api.iconify.design/logos/aws-cloudwatch.svg` | 1:1 |
| CodeBuild | `logos:aws-codebuild` | `https://api.iconify.design/logos/aws-codebuild.svg` | 1:1 |
| CodeCommit | `logos:aws-codecommit` | `https://api.iconify.design/logos/aws-codecommit.svg` | 1:1 |
| CodeDeploy | `logos:aws-codedeploy` | `https://api.iconify.design/logos/aws-codedeploy.svg` | 1:1 |
| CodePipeline | `logos:aws-codepipeline` | `https://api.iconify.design/logos/aws-codepipeline.svg` | 1:1 |
| Cognito | `logos:aws-cognito` | `https://api.iconify.design/logos/aws-cognito.svg` | 1:1 |
| Config | `logos:aws-config` | `https://api.iconify.design/logos/aws-config.svg` | 1:1 |
| DocumentDB | `logos:aws-documentdb` | `https://api.iconify.design/logos/aws-documentdb.svg` | 1:1 |
| DynamoDB | `logos:aws-dynamodb` | `https://api.iconify.design/logos/aws-dynamodb.svg` | 1:1 |
| EC2 | `logos:aws-ec2` | `https://api.iconify.design/logos/aws-ec2.svg` | 1:1 |
| ECS | `logos:aws-ecs` | `https://api.iconify.design/logos/aws-ecs.svg` | 1:1 |
| EKS | `logos:aws-eks` | `https://api.iconify.design/logos/aws-eks.svg` | 1:1 |
| ElastiCache | `logos:aws-elasticache` | `https://api.iconify.design/logos/aws-elasticache.svg` | 1:1 |
| Elastic Beanstalk | `logos:aws-elastic-beanstalk` | `https://api.iconify.design/logos/aws-elastic-beanstalk.svg` | 1:1 |
| ELB | `logos:aws-elb` | `https://api.iconify.design/logos/aws-elb.svg` | 1:1 |
| EventBridge | `logos:aws-eventbridge` | `https://api.iconify.design/logos/aws-eventbridge.svg` | 1:1 |
| Fargate | `logos:aws-fargate` | `https://api.iconify.design/logos/aws-fargate.svg` | 1:1 |
| Glacier | `logos:aws-glacier` | `https://api.iconify.design/logos/aws-glacier.svg` | 1:1 |
| Glue | `logos:aws-glue` | `https://api.iconify.design/logos/aws-glue.svg` | 1:1 |
| IAM | `logos:aws-iam` | `https://api.iconify.design/logos/aws-iam.svg` | 1:1 |
| Keyspaces | `logos:aws-keyspaces` | `https://api.iconify.design/logos/aws-keyspaces.svg` | 1:1 |
| Kinesis | `logos:aws-kinesis` | `https://api.iconify.design/logos/aws-kinesis.svg` | 1:1 |
| KMS | `logos:aws-kms` | `https://api.iconify.design/logos/aws-kms.svg` | 1:1 |
| Lake Formation | `logos:aws-lake-formation` | `https://api.iconify.design/logos/aws-lake-formation.svg` | 1:1 |
| Lambda | `logos:aws-lambda` | `https://api.iconify.design/logos/aws-lambda.svg` | 1:1 |
| Lightsail | `logos:aws-lightsail` | `https://api.iconify.design/logos/aws-lightsail.svg` | 1:1 |
| MQ | `logos:aws-mq` | `https://api.iconify.design/logos/aws-mq.svg` | 1:1 |
| MSK | `logos:aws-msk` | `https://api.iconify.design/logos/aws-msk.svg` | 1:1 |
| Neptune | `logos:aws-neptune` | `https://api.iconify.design/logos/aws-neptune.svg` | 1:1 |
| OpenSearch | `logos:aws-open-search` | `https://api.iconify.design/logos/aws-open-search.svg` | 1:1 |
| OpsWorks | `logos:aws-opsworks` | `https://api.iconify.design/logos/aws-opsworks.svg` | 1:1 |
| QuickSight | `logos:aws-quicksight` | `https://api.iconify.design/logos/aws-quicksight.svg` | 1:1 |
| RDS | `logos:aws-rds` | `https://api.iconify.design/logos/aws-rds.svg` | 1:1 |
| Redshift | `logos:aws-redshift` | `https://api.iconify.design/logos/aws-redshift.svg` | 1:1 |
| Route 53 | `logos:aws-route53` | `https://api.iconify.design/logos/aws-route53.svg` | 1:1 |
| S3 | `logos:aws-s3` | `https://api.iconify.design/logos/aws-s3.svg` | 1:1 |
| Secrets Manager | `logos:aws-secrets-manager` | `https://api.iconify.design/logos/aws-secrets-manager.svg` | 1:1 |
| SES | `logos:aws-ses` | `https://api.iconify.design/logos/aws-ses.svg` | 1:1 |
| Shield | `logos:aws-shield` | `https://api.iconify.design/logos/aws-shield.svg` | 1:1 |
| SNS | `logos:aws-sns` | `https://api.iconify.design/logos/aws-sns.svg` | 1:1 |
| SQS | `logos:aws-sqs` | `https://api.iconify.design/logos/aws-sqs.svg` | 1:1 |
| Step Functions | `logos:aws-step-functions` | `https://api.iconify.design/logos/aws-step-functions.svg` | 1:1 |
| Systems Manager | `logos:aws-systems-manager` | `https://api.iconify.design/logos/aws-systems-manager.svg` | 1:1 |
| Timestream | `logos:aws-timestream` | `https://api.iconify.design/logos/aws-timestream.svg` | 1:1 |
| VPC | `logos:aws-vpc` | `https://api.iconify.design/logos/aws-vpc.svg` | 1:1 |
| WAF | `logos:aws-waf` | `https://api.iconify.design/logos/aws-waf.svg` | 1:1 |
| X-Ray | `logos:aws-xray` | `https://api.iconify.design/logos/aws-xray.svg` | 1:1 |
| Amplify | `logos:aws-amplify` | `https://api.iconify.design/logos/aws-amplify.svg` | 1:1 |
| CodeStar | `logos:aws-codestar` | `https://api.iconify.design/logos/aws-codestar.svg` | 1:1 |
| DynamoDB (devicon) | `devicon:dynamodb` | `https://api.iconify.design/devicon/dynamodb.svg` | 1:1 |

### 1.2 Google Cloud

`gcp` 图标集提供 214 个 GCP 服务专用图标，命名最完整；`logos`/`devicon` 仅提供通用云图标。

**`gcp:` 服务图标**（推荐用于 GCP 服务级图标）：

| 服务 | icon-pack 引用 | SVG URL |
|------|---------------|---------|
| Compute Engine | `gcp:compute-engine` | `https://api.iconify.design/gcp/compute-engine.svg` |
| Cloud Functions | `gcp:cloud-functions` | `https://api.iconify.design/gcp/cloud-functions.svg` |
| Cloud Run | `gcp:cloud-run` | `https://api.iconify.design/gcp/cloud-run.svg` |
| Cloud SQL | `gcp:cloud-sql` | `https://api.iconify.design/gcp/cloud-sql.svg` |
| BigQuery | `gcp:bigquery` | `https://api.iconify.design/gcp/bigquery.svg` |
| Cloud Storage | `gcp:cloud-storage` | `https://api.iconify.design/gcp/cloud-storage.svg` |
| Pub/Sub | `gcp:pubsub` | `https://api.iconify.design/gcp/pubsub.svg` |
| Kubernetes Engine (GKE) | `gcp:google-kubernetes-engine` | `https://api.iconify.design/gcp/google-kubernetes-engine.svg` |
| App Engine | `gcp:app-engine` | `https://api.iconify.design/gcp/app-engine.svg` |
| Cloud Build | `gcp:cloud-build` | `https://api.iconify.design/gcp/cloud-build.svg` |
| Cloud Spanner | `gcp:cloud-spanner` | `https://api.iconify.design/gcp/cloud-spanner.svg` |
| Firestore | `gcp:firestore` | `https://api.iconify.design/gcp/firestore.svg` |
| Cloud Load Balancing | `gcp:cloud-load-balancing` | `https://api.iconify.design/gcp/cloud-load-balancing.svg` |
| Cloud CDN | `gcp:cloud-cdn` | `https://api.iconify.design/gcp/cloud-cdn.svg` |
| Cloud Armor | `gcp:cloud-armor` | `https://api.iconify.design/gcp/cloud-armor.svg` |
| Cloud DNS | `gcp:cloud-dns` | `https://api.iconify.design/gcp/cloud-dns.svg` |
| Memorystore | `gcp:memorystore` | `https://api.iconify.design/gcp/memorystore.svg` |
| Cloud Logging | `gcp:cloud-logging` | `https://api.iconify.design/gcp/cloud-logging.svg` |
| Cloud Monitoring | `gcp:cloud-monitoring` | `https://api.iconify.design/gcp/cloud-monitoring.svg` |
| IAM | `gcp:identity-and-access-management` | `https://api.iconify.design/gcp/identity-and-access-management.svg` |

**`logos:` / `devicon:` 通用云图标**：

| 服务 | icon-pack 引用 | SVG URL | 宽高比 |
|------|---------------|---------|--------|
| Google Cloud (通用) | `logos:google-cloud` | `https://api.iconify.design/logos/google-cloud.svg` | 1:1 |
| Cloud Functions | `logos:google-cloud-functions` | `https://api.iconify.design/logos/google-cloud-functions.svg` | 1:1 |
| Cloud Run | `logos:google-cloud-run` | `https://api.iconify.design/logos/google-cloud-run.svg` | 1:1 |
| Google Cloud (devicon) | `devicon:googlecloud` | `https://api.iconify.design/devicon/googlecloud.svg` | 1:1 |

### 1.3 Azure

| 服务 | icon-pack 引用 | SVG URL | 宽高比 |
|------|---------------|---------|--------|
| Azure (通用) | `logos:microsoft-azure` | `https://api.iconify.design/logos/microsoft-azure.svg` | 1:1 |
| Azure (devicon) | `devicon:azure` | `https://api.iconify.design/devicon/azure.svg` | 1:1 |
| Azure DevOps | `devicon:azuredevops` | `https://api.iconify.design/devicon/azuredevops.svg` | 1:1 |
| Azure Data Factory | `devicon:azuredatafactory` | `https://api.iconify.design/devicon/azuredatafactory.svg` | 1:1 |
| Azure SQL Database | `devicon:azuresqldatabase` | `https://api.iconify.design/devicon/azuresqldatabase.svg` | 1:1 |

### 1.4 其他云平台

| 平台 | icon-pack 引用 | SVG URL |
|------|---------------|---------|
| Cloudflare | `logos:cloudflare-icon` | `https://api.iconify.design/logos/cloudflare-icon.svg` |
| Vercel | `logos:vercel-icon` | `https://api.iconify.design/logos/vercel-icon.svg` |
| Netlify | `logos:netlify-icon` | `https://api.iconify.design/logos/netlify-icon.svg` |
| DigitalOcean | `logos:digital-ocean` | `https://api.iconify.design/logos/digital-ocean.svg` |
| Heroku | `logos:heroku-icon` | `https://api.iconify.design/logos/heroku-icon.svg` |
| Firebase | `logos:firebase-icon` | `https://api.iconify.design/logos/firebase-icon.svg` |
| Supabase | `logos:supabase-icon` | `https://api.iconify.design/logos/supabase-icon.svg` |
| Railway | `devicon:railway` | `https://api.iconify.design/devicon/railway.svg` |
| Fly.io | `logos:fly-icon` | `https://api.iconify.design/logos/fly-icon.svg` |
| PlanetScale | `logos:planetscale` | `https://api.iconify.design/logos/planetscale.svg` |
| IPFS | `logos:ipfs` | `https://api.iconify.design/logos/ipfs.svg` ⚠ |

> ⚠️ `logos:ipfs` 宽高比 ~3:1（严重横向扁平），严禁同时设 `w` 和 `h`。

---

## 2. 编程语言 (Programming Languages)

使用 **devicon**（首选，命名最简洁）或 **skill-icons**（有 light/dark 变体）。

| 语言 | devicon (首选) | skill-icons | logos |
|------|---------------|-------------|-------|
| Python | `devicon:python` | `skill-icons:python-light` / `python-dark` | `logos:python` |
| JavaScript | `devicon:javascript` | `skill-icons:javascript` | `logos:javascript` |
| TypeScript | `devicon:typescript` | `skill-icons:typescript` | `logos:typescript` |
| Java | `devicon:java` | `skill-icons:java-light` / `java-dark` | `logos:java` |
| Go | `devicon:go` | `skill-icons:golang` | `logos:go` |
| Rust | `devicon:rust` | `skill-icons:rust` | `logos:rust` |
| C# | `devicon:csharp` | — | — |
| C++ | `devicon:cplusplus` | `skill-icons:cpp` | — |
| C | `devicon:c` | — | — |
| Kotlin | `devicon:kotlin` | `skill-icons:kotlin-light` / `kotlin-dark` | `logos:kotlin` |
| Swift | `devicon:swift` | `skill-icons:swift` | `logos:swift` |
| Ruby | `devicon:ruby` | `skill-icons:ruby` | `logos:ruby` |
| PHP | `devicon:php` | `skill-icons:php-light` / `php-dark` | `logos:php` |
| Dart | `devicon:dart` | `skill-icons:dart-light` / `dart-dark` | `logos:dart` |
| Lua | `devicon:lua` | — | `logos:lua` |
| Scala | `devicon:scala` | — | `logos:scala` |
| Haskell | `devicon:haskell` | — | `logos:haskell` |
| Elixir | `devicon:elixir` | — | `logos:elixir` |
| Clojure | `devicon:clojure` | — | `logos:clojure` |
| R | `devicon:r` | — | `logos:r-lang` |
| MATLAB | `devicon:matlab` | — | `logos:matlab` |
| Groovy | `devicon:groovy` | — | `logos:groovy` |
| Objective-C | `devicon:objectivec` | — | `logos:objective-c` |
| Zig | `devicon:zig` | — | `logos:zig` |
| Nim | `devicon:nim` | — | `logos:nim` |
| OCaml | `devicon:ocaml` | — | `logos:ocaml` |
| Julia | `devicon:julia` | — | `logos:julia` |
| F# | `devicon:fsharp` | — | — |
| Erlang | `devicon:erlang` | — | `logos:erlang` |
| Solidity | — | `skill-icons:solidity` | — |
| GraphQL | — | `skill-icons:graphql-light` / `graphql-dark` | `logos:graphql` |
| Bash | `devicon:bash` | `skill-icons:bash-light` / `bash-dark` | — |
| PowerShell | — | — | `logos:powershell` |

**SVG URL 示例**（devicon）：
```
https://api.iconify.design/devicon/python.svg
https://api.iconify.design/devicon/go.svg
https://api.iconify.design/devicon/rust.svg
```

---

## 3. 运行时与后端框架 (Runtimes & Backend Frameworks)

| 技术 | devicon (首选) | skill-icons | logos |
|------|---------------|-------------|-------|
| Node.js | `devicon:nodejs` | `skill-icons:nodejs-light` / `nodejs-dark` | `logos:nodejs` |
| Deno | — | `skill-icons:deno-light` / `deno-dark` | `logos:deno` |
| Bun | `devicon:bun` | `skill-icons:bun-light` / `bun-dark` | `logos:bun` |
| .NET | `devicon:dotnetcore` | `skill-icons:dotnet` | `logos:dotnet` |
| Spring Boot | `devicon:spring` | `skill-icons:spring-light` / `spring-dark` | `logos:spring-icon` |
| Django | `devicon:django` | `skill-icons:django` | `logos:django-icon` |
| Flask | `devicon:flask` | `skill-icons:flask-light` / `flask-dark` | `logos:flask` |
| FastAPI | `devicon:fastapi` | `skill-icons:fastapi` | `logos:fastapi-icon` |
| Rails | — | `skill-icons:rails` | `logos:rails` |
| Laravel | `devicon:laravel` | `skill-icons:laravel-light` / `laravel-dark` | `logos:laravel` |
| Express | `devicon:express` | — | `logos:express` |
| NestJS | `devicon:nestjs` | `skill-icons:nestjs-light` / `nestjs-dark` | `logos:nestjs` |
| GraphQL Yoga | — | — | `logos:graphql-yoga` |
| tRPC | — | — | `logos:trpc` |
| Hono | — | — | `logos:hono` |
| Prisma | `devicon:prisma` | `skill-icons:prisma` | `logos:prisma` |
| Drizzle ORM | — | — | `logos:drizzle-icon` |
| TypeORM | `devicon:typeorm` | — | `logos:typeorm` |
| Sequelize | `devicon:sequelize` | `skill-icons:sequelize-light` / `sequelize-dark` | `logos:sequelize` |
| Mongoose | `devicon:mongoose` | — | — |

---

## 4. 数据库与存储 (Databases & Storage)

| 数据库 | devicon (首选) | skill-icons | logos |
|--------|---------------|-------------|-------|
| PostgreSQL | `devicon:postgresql` | `skill-icons:postgresql-light` / `postgresql-dark` | `logos:postgresql` |
| MySQL | `devicon:mysql` | `skill-icons:mysql-light` / `mysql-dark` | `logos:mysql-icon` |
| MongoDB | `devicon:mongodb` | `skill-icons:mongodb` | `logos:mongodb-icon` |
| Redis | `devicon:redis` | `skill-icons:redis-light` / `redis-dark` | `logos:redis` ⚠ |
| SQLite | `devicon:sqlite` | `skill-icons:sqlite` | `logos:sqlite` |
| MariaDB | `devicon:mariadb` | — | `logos:mariadb-icon` |
| Cassandra | `devicon:cassandra` | `skill-icons:cassandra-light` / `cassandra-dark` | `logos:cassandra` |
| Neo4j | `devicon:neo4j` | — | `logos:neo4j` |
| Elasticsearch | `devicon:elasticsearch` | `skill-icons:elasticsearch-light` / `elasticsearch-dark` | `logos:elasticsearch` |
| InfluxDB | `devicon:influxdb` | — | `logos:influxdb-icon` |
| ClickHouse | `devicon:clickhouse` | — | — |
| ClickHouse | `devicon:clickhouse` | — | — |
| DuckDB | `devicon:duckdb` | — | — |
| Snowflake | — | — | `logos:snowflake-icon` |
| BigQuery | — | — | `logos:bigquery` |
| Oracle | `devicon:oracle` | — | `logos:oracle` |
| CockroachDB | `devicon:cockroach` | — | `logos:cockroachdb` |
| TiDB | — | — | `logos:tidb` |
| Couchbase | `devicon:couchbase` | — | `logos:couchbase` |
| CouchDB | `devicon:couchdb` | — | — |
| FoundationDB | `devicon:foundationdb` | — | — |
| Ceph | `devicon:ceph` | — | — |

> ⚠ `logos:redis` 宽高比 ~3.2:1，在 `@{ img: }` 中严禁同时设 `w` 和 `h`。替代方案：用 `logos:heroku-redis`（更方）或 `devicon:redis`（1:1）。

---

## 5. DevOps 与 CI/CD

### 5.1 CI/CD 平台

| 工具 | devicon (首选) | skill-icons | logos |
|------|---------------|-------------|-------|
| GitHub Actions | `devicon:githubactions` | `skill-icons:githubactions-light` / `githubactions-dark` | `logos:github-actions` |
| GitLab CI | `devicon:gitlab` | `skill-icons:gitlab-light` / `gitlab-dark` | `logos:gitlab-icon` |
| Jenkins | `devicon:jenkins` | `skill-icons:jenkins-light` / `jenkins-dark` | `logos:jenkins` |
| CircleCI | — | — | `logos:circleci` |
| Travis CI | `devicon:travis` | — | `logos:travis-ci` |
| Bamboo | `devicon:bamboo` | — | `logos:bamboo` |
| ArgoCD | `devicon:argocd` | — | `logos:argo-icon` |
| Spinnaker | — | — | `logos:spinnaker` |
| Drone CI | — | — | `logos:drone` |
| TeamCity | `devicon:teamcity` | — | `logos:teamcity` |
| Codecov | — | — | `logos:codecov` |
| Coveralls | — | — | `logos:coveralls` |

### 5.2 基础设施即代码 (IaC)

| 工具 | devicon (首选) | skill-icons | logos |
|------|---------------|-------------|-------|
| Terraform | `devicon:terraform` | `skill-icons:terraform-light` / `terraform-dark` | `logos:terraform-icon` |
| Ansible | `devicon:ansible` | `skill-icons:ansible` | `logos:ansible` |
| Pulumi | `devicon:pulumi` | — | `logos:pulumi` |
| Chef | — | — | `logos:chef` |
| Puppet | — | — | `logos:puppet-icon` |
| Vagrant | `devicon:vagrant` | — | `logos:vagrant-icon` |
| Packer | `devicon:packer` | — | `logos:packer` |
| OpenTofu | — | — | `logos:opentofu` |
| Crossplane | — | — | `logos:crossplane` |

### 5.3 容器与编排

| 工具 | devicon (首选) | skill-icons | logos |
|------|---------------|-------------|-------|
| Docker | `devicon:docker` | `skill-icons:docker` | `logos:docker-icon` |
| Kubernetes | `devicon:kubernetes` | `skill-icons:kubernetes` | `logos:kubernetes` |
| Helm | `devicon:helm` | — | `logos:helm` |
| OpenShift | — | `skill-icons:openshift` | `logos:openshift` |
| Rancher | `devicon:rancher` | — | `logos:rancher-icon` |
| k3s | `devicon:k3s` | — | — |
| Podman | `devicon:podman` | — | — |
| containerd | `devicon:containerd` | — | — |
| Istio | `devicon:istio` | — | — |
| Envoy | `devicon:envoy` | — | `logos:envoy-icon` |
| Linkerd | `devicon:linkerd` | — | `logos:linkerd` |
| Traefik | `devicon:traefikproxy` | — | — |
| Consul | `devicon:consul` | — | `logos:consul` |
| Vagrant | `devicon:vagrant` | — | `logos:vagrant-icon` |

---

## 6. 可观测性 (Observability)

| 工具 | devicon (首选) | skill-icons | logos |
|------|---------------|-------------|-------|
| Grafana | `devicon:grafana` | `skill-icons:grafana-light` / `grafana-dark` | `logos:grafana` |
| Prometheus | `devicon:prometheus` | `skill-icons:prometheus` | `logos:prometheus` |
| Datadog | `devicon:datadog` | — | `logos:datadog-icon` |
| New Relic | `devicon:newrelic` | — | — |
| Sentry | `devicon:sentry` | `skill-icons:sentry` | `logos:sentry-icon` |
| Kibana | `devicon:kibana` | — | `logos:kibana` |
| Logstash | `devicon:logstash` | — | `logos:logstash` |
| Jaeger | `devicon:jaegertracing` | — | — |
| Splunk | — | — | `logos:splunk` |
| Dynatrace | `devicon:dynatrace` | — | `logos:dynatrace-icon` |
| OpenTelemetry | `devicon:opentelemetry` | — | `logos:opentelemetry` |
| Thanos | — | — | `logos:thanos` |
| Loki | — | — | `logos:loki-icon` |
| Mimir | — | — | `logos:mimir-icon` |
| Tempo | — | — | `logos:tempo` |
| SigNoz | — | — | `logos:signoz` |

---

## 7. 消息队列与流处理 (Messaging & Streaming)

| 服务 | devicon (首选) | skill-icons | logos |
|------|---------------|-------------|-------|
| Apache Kafka | `devicon:apachekafka` | `skill-icons:kafka` | `logos:kafka-icon` |
| RabbitMQ | `devicon:rabbitmq` | `skill-icons:rabbitmq-light` / `rabbitmq-dark` | `logos:rabbitmq-icon` |
| Apache Pulsar | `devicon:pulsar` | — | — |
| NATS | `devicon:nats` | — | `logos:nats-icon` |
| ZeroMQ | — | — | `logos:zeromq` |
| Apache Flink | — | — | `logos:apache-flink-icon` |
| Apache Spark | `devicon:apachespark` | — | `logos:apache-spark` |
| Apache Storm | — | — | `logos:apache-storm` |

---

## 8. AI / ML / LLM

| 技术 | devicon (首选) | skill-icons | logos |
|------|---------------|-------------|-------|
| OpenAI | — | — | `logos:openai-icon` |
| Anthropic | — | — | `logos:anthropic-icon` |
| TensorFlow | `devicon:tensorflow` | `skill-icons:tensorflow-light` / `tensorflow-dark` | `logos:tensorflow` |
| PyTorch | `devicon:pytorch` | `skill-icons:pytorch-light` / `pytorch-dark` | `logos:pytorch-icon` |
| Keras | `devicon:keras` | — | — |
| Hugging Face | `devicon:huggingface` | — | — |
| Jupyter | `devicon:jupyter` | — | `logos:jupyter` |
| LangChain | — | — | `logos:langchain` |
| LlamaIndex | — | — | `logos:llamaindex` |
| Chroma | — | — | `logos:chroma` |
| Pinecone | — | — | `logos:pinecone-icon` |
| Qdrant | — | — | `logos:qdrant-icon` |
| Weaviate | — | — | `logos:weaviate` |
| Milvus | — | — | `logos:milvus` |
| Ollama | `devicon:ollama` | — | — |
| Mistral AI | — | — | `logos:mistral-ai-icon` |
| Midjourney | — | — | `logos:midjourney` |
| Stable Diffusion | — | `skill-icons:stable-diffusion` | `logos:stable-diffusion` |
| Gradio | — | — | `logos:gradio-icon` |
| Streamlit | `devicon:streamlit` | — | `logos:streamlit` |
| MLflow | — | — | `logos:mlflow` |
| NumPy | `devicon:numpy` | — | `logos:numpy` |
| Pandas | `devicon:pandas` | — | `logos:pandas-icon` |
| NVIDIA | — | — | `logos:nvidia` |
| CUDA | `devicon:cuda` | — | — |

---

## 9. 前端框架与工具 (Frontend)

### 9.1 框架与元框架

| 框架 | devicon (首选) | skill-icons | logos |
|------|---------------|-------------|-------|
| React | `devicon:react` | `skill-icons:react-light` / `react-dark` | `logos:react` |
| Next.js | `devicon:nextjs` | `skill-icons:nextjs-light` / `nextjs-dark` | `logos:nextjs-icon` |
| Vue.js | `devicon:vuejs` | `skill-icons:vuejs-light` / `vuejs-dark` | `logos:vue` |
| Nuxt.js | `devicon:nuxtjs` | `skill-icons:nuxtjs-light` / `nuxtjs-dark` | — |
| Angular | `devicon:angular` | `skill-icons:angular-light` / `angular-dark` | `logos:angular-icon` |
| Svelte | `devicon:svelte` | `skill-icons:svelte` | `logos:svelte-icon` |
| SvelteKit | — | — | `logos:svelte-kit` |
| SolidJS | `devicon:solidjs` | `skill-icons:solidjs-light` / `solidjs-dark` | `logos:solidjs-icon` |
| Astro | `devicon:astro` | `skill-icons:astro` | `logos:astro-icon` |
| Qwik | `devicon:qwik` | — | `logos:qwik-icon` |
| Remix | `devicon:remix` | `skill-icons:remix-light` / `remix-dark` | `logos:remix-icon` |
| Gatsby | `devicon:gatsby` | `skill-icons:gatsby` | `logos:gatsby` |
| Ember | `devicon:ember` | `skill-icons:ember` | `logos:ember` |
| jQuery | `devicon:jquery` | `skill-icons:jquery` | `logos:jquery` |
| Backbone.js | `devicon:backbonejs` | — | `logos:backbone-icon` |
| React Native | `devicon:reactnative` | — | — |
| Flutter | `devicon:flutter` | `skill-icons:flutter-light` / `flutter-dark` | `logos:flutter` |
| Electron | `devicon:electron` | — | `logos:electron` |

### 9.2 CSS / UI 框架

| 框架 | devicon (首选) | skill-icons | logos |
|------|---------------|-------------|-------|
| Tailwind CSS | `devicon:tailwindcss` | `skill-icons:tailwindcss-light` / `tailwindcss-dark` | `logos:tailwindcss-icon` |
| Bootstrap | `devicon:bootstrap` | `skill-icons:bootstrap` | `logos:bootstrap` |
| Material UI | — | `skill-icons:materialui-light` / `materialui-dark` | `logos:material-ui` |
| Chakra UI | `devicon:chakraui` | — | — |
| Ant Design | `devicon:antdesign` | — | `logos:ant-design` |
| shadcn/ui | — | — | `logos:shadcnui` |
| Radix UI | — | — | `logos:radix-ui` |
| Vuetify | `devicon:vuetify` | `skill-icons:vuetify-light` / `vuetify-dark` | `logos:vuetifyjs` |
| UnoCSS | — | — | `logos:unocss` |

### 9.3 构建与测试工具

| 工具 | devicon (首选) | skill-icons | logos |
|------|---------------|-------------|-------|
| Vite | `devicon:vite` | `skill-icons:vite-light` / `vite-dark` | `logos:vite` |
| webpack | `devicon:webpack` | `skill-icons:webpack-light` / `webpack-dark` | `logos:webpack` |
| Rollup | `devicon:rollup` | — | `logos:rollupjs` |
| esbuild | — | — | `logos:esbuild` |
| Turbopack | — | — | `logos:turbopack-icon` |
| Babel | `devicon:babel` | — | `logos:babel` |
| SWC | `devicon:swc` | — | — |
| Vitest | `devicon:vitest` | `skill-icons:vitest-light` / `vitest-dark` | `logos:vitest` |
| Jest | — | `skill-icons:jest` | `logos:jest` |
| Playwright | `devicon:playwright` | — | `logos:playwright` |
| Cypress | `devicon:cypressio` | `skill-icons:cypress-light` / `cypress-dark` | `logos:cypress-icon` |
| Testing Library | — | — | `logos:testing-library` |
| Storybook | `devicon:storybook` | — | `logos:storybook-icon` |

---

## 10. 工具与平台 (Tools & Platforms)

### 10.1 版本控制与协作

| 工具 | devicon | skill-icons | logos | codicon |
|------|---------|-------------|-------|---------|
| GitHub | `devicon:github` | `skill-icons:github-light` / `github-dark` | `logos:github-icon` | `codicon:github` |
| GitLab | `devicon:gitlab` | `skill-icons:gitlab-light` / `gitlab-dark` | `logos:gitlab-icon` | — |
| Bitbucket | `devicon:bitbucket` | `skill-icons:bitbucket-light` / `bitbucket-dark` | `logos:bitbucket` | — |
| Git (通用) | `devicon:git` | `skill-icons:git` | `logos:git-icon` | `codicon:git-branch` |
| GitHub Copilot | `devicon:githubcopilot` | — | `logos:github-copilot` | — |
| Gitea | `devicon:gitea` | — | — | — |

### 10.2 协作与项目管理

| 工具 | devicon | logos |
|------|---------|-------|
| Figma | `devicon:figma` | `logos:figma` |
| Notion | `devicon:notion` | `logos:notion-icon` |
| Slack | `devicon:slack` | `logos:slack-icon` |
| Jira | `devicon:jira` | `logos:jira` |
| Linear | — | `logos:linear-icon` |
| Confluence | `devicon:confluence` | `logos:confluence` |
| Trello | `devicon:trello` | `logos:trello` |
| Asana | — | `logos:asana-icon` |
| Discord | — | `logos:discord-icon` |
| Teams | — | `logos:microsoft-teams` |

### 10.3 API 与网络

| 工具 | devicon | skill-icons | logos |
|------|---------|-------------|-------|
| Postman | `devicon:postman` | `skill-icons:postman` | `logos:postman-icon` |
| Insomnia | `devicon:insomnia` | — | `logos:insomnia` |
| Swagger | `devicon:swagger` | — | `logos:swagger` |
| Nginx | `devicon:nginx` | `skill-icons:nginx` | `logos:nginx` ⚠️ |
| Apache | `devicon:apache` | — | `logos:apache` |
| Caddy | — | — | `logos:caddy` |
| HAProxy | `devicon:haproxy` | — | — |
| Cloudflare | `devicon:cloudflare` | `skill-icons:cloudflare-light` / `cloudflare-dark` | `logos:cloudflare-icon` |

> ⚠️ `logos:nginx` 宽高比 ~3.5:1（严重横向扁平），严禁同时设 `w` 和 `h`。推荐替代：`devicon:nginx`（1:1）。

### 10.4 安全与身份认证

| 工具 | devicon | logos |
|------|---------|-------|
| Okta | `devicon:okta` | `logos:okta-icon` |
| Auth0 | — | `logos:auth0-icon` |
| SuperTokens | — | `logos:supertokens-icon` |
| Clerk | — | `logos:clerk` |
| Vault | `devicon:vault` | `logos:vault` |
| Snyk | — | `logos:snyk` |
| SonarQube | `devicon:sonarqube` | `logos:sonarqube` |

### 10.5 数据工程

| 工具 | devicon | logos |
|------|---------|-------|
| Apache Airflow | `devicon:apacheairflow` | `logos:airflow-icon` |
| dbt | `devicon:dbt` | `logos:dbt-icon` |
| Apache Hadoop | `devicon:hadoop` | — |
| Apache Hive | — | `logos:hive` |
| Presto | `devicon:presto` | `logos:presto` |
| Trino | — | `logos:trino` |
| Apache NiFi | `devicon:nifi` | — |
| Databricks | `devicon:databricks` | — |
| Fivetran | — | `logos:fivetran` |
| Airbyte | — | `logos:airbyte` |

---

## 11. 开发概念 (codicon — IDE/Git/概念图标)

codicon 是 VS Code 使用的图标集，600+ 图标。适用于表示 **Git 操作、开发概念、IDE 功能**等抽象操作。

### 11.1 Git 操作

| 概念 | codicon 引用 | SVG URL |
|------|------------|---------|
| Git Branch | `codicon:git-branch` | `https://api.iconify.design/codicon/git-branch.svg` |
| Git Commit | `codicon:git-commit` | `https://api.iconify.design/codicon/git-commit.svg` |
| Git Merge | `codicon:git-merge` | `https://api.iconify.design/codicon/git-merge.svg` |
| Pull Request | `codicon:git-pull-request` | `https://api.iconify.design/codicon/git-pull-request.svg` |
| PR Draft | `codicon:git-pull-request-draft` | `https://api.iconify.design/codicon/git-pull-request-draft.svg` |
| PR Closed | `codicon:git-pull-request-closed` | `https://api.iconify.design/codicon/git-pull-request-closed.svg` |
| PR Create | `codicon:git-pull-request-create` | `https://api.iconify.design/codicon/git-pull-request-create.svg` |
| Git Fetch | `codicon:git-fetch` | `https://api.iconify.design/codicon/git-fetch.svg` |
| Git Stash | `codicon:git-stash` | `https://api.iconify.design/codicon/git-stash.svg` |
| Git Compare | `codicon:git-compare` | `https://api.iconify.design/codicon/git-compare.svg` |
| Repo | `codicon:repo` | `https://api.iconify.design/codicon/repo.svg` |
| Repo Clone | `codicon:repo-clone` | `https://api.iconify.design/codicon/repo-clone.svg` |
| Repo Push | `codicon:repo-push` | `https://api.iconify.design/codicon/repo-push.svg` |
| Repo Pull | `codicon:repo-pull` | `https://api.iconify.design/codicon/repo-pull.svg` |
| Repo Forked | `codicon:repo-forked` | `https://api.iconify.design/codicon/repo-forked.svg` |

### 11.2 Terminal / Shell

| 概念 | codicon 引用 | SVG URL |
|------|------------|---------|
| Terminal | `codicon:terminal` | `https://api.iconify.design/codicon/terminal.svg` |
| Terminal Bash | `codicon:terminal-bash` | `https://api.iconify.design/codicon/terminal-bash.svg` |
| Terminal Linux | `codicon:terminal-linux` | `https://api.iconify.design/codicon/terminal-linux.svg` |
| Terminal PowerShell | `codicon:terminal-powershell` | `https://api.iconify.design/codicon/terminal-powershell.svg` |

### 11.3 Debug

| 概念 | codicon 引用 | SVG URL |
|------|------------|---------|
| Debug | `codicon:debug` | `https://api.iconify.design/codicon/debug.svg` |
| Debug Start | `codicon:debug-start` | `https://api.iconify.design/codicon/debug-start.svg` |
| Debug Stop | `codicon:debug-stop` | `https://api.iconify.design/codicon/debug-stop.svg` |
| Debug Pause | `codicon:debug-pause` | `https://api.iconify.design/codicon/debug-pause.svg` |
| Debug Continue | `codicon:debug-continue` | `https://api.iconify.design/codicon/debug-continue.svg` |
| Debug Step Over | `codicon:debug-step-over` | `https://api.iconify.design/codicon/debug-step-over.svg` |
| Debug Step Into | `codicon:debug-step-into` | `https://api.iconify.design/codicon/debug-step-into.svg` |
| Debug Console | `codicon:debug-console` | `https://api.iconify.design/codicon/debug-console.svg` |
| Breakpoint | `codicon:debug-breakpoint` | `https://api.iconify.design/codicon/debug-breakpoint.svg` |
| Breakpoint Conditional | `codicon:debug-breakpoint-conditional` | `https://api.iconify.design/codicon/debug-breakpoint-conditional.svg` |

### 11.4 文件与编辑器操作

| 概念 | codicon 引用 | SVG URL |
|------|------------|---------|
| File | `codicon:file` | `https://api.iconify.design/codicon/file.svg` |
| File Code | `codicon:file-code` | `https://api.iconify.design/codicon/file-code.svg` |
| File Text | `codicon:file-text` | `https://api.iconify.design/codicon/file-text.svg` |
| File Binary | `codicon:file-binary` | `https://api.iconify.design/codicon/file-binary.svg` |
| Folder | `codicon:folder` | `https://api.iconify.design/codicon/folder.svg` |
| Folder Opened | `codicon:folder-opened` | `https://api.iconify.design/codicon/folder-opened.svg` |
| New File | `codicon:new-file` | `https://api.iconify.design/codicon/new-file.svg` |
| New Folder | `codicon:new-folder` | `https://api.iconify.design/codicon/new-folder.svg` |
| Go to File | `codicon:go-to-file` | `https://api.iconify.design/codicon/go-to-file.svg` |
| Search | `codicon:search` | `https://api.iconify.design/codicon/search.svg` |
| Settings | `codicon:settings` | `https://api.iconify.design/codicon/settings.svg` |
| Settings Gear | `codicon:settings-gear` | `https://api.iconify.design/codicon/settings-gear.svg` |

### 11.5 代码符号

| 概念 | codicon 引用 | SVG URL |
|------|------------|---------|
| Symbol Class | `codicon:symbol-class` | `https://api.iconify.design/codicon/symbol-class.svg` |
| Symbol Method | `codicon:symbol-method` | `https://api.iconify.design/codicon/symbol-method.svg` |
| Symbol Interface | `codicon:symbol-interface` | `https://api.iconify.design/codicon/symbol-interface.svg` |
| Symbol Variable | `codicon:symbol-variable` | `https://api.iconify.design/codicon/symbol-variable.svg` |
| Symbol Constant | `codicon:symbol-constant` | `https://api.iconify.design/codicon/symbol-constant.svg` |
| Symbol Property | `codicon:symbol-property` | `https://api.iconify.design/codicon/symbol-property.svg` |
| Symbol Field | `codicon:symbol-field` | `https://api.iconify.design/codicon/symbol-field.svg` |
| Symbol Enum | `codicon:symbol-enum` | `https://api.iconify.design/codicon/symbol-enum.svg` |
| Symbol String | `codicon:symbol-string` | `https://api.iconify.design/codicon/symbol-string.svg` |
| Symbol Numeric | `codicon:symbol-numeric` | `https://api.iconify.design/codicon/symbol-numeric.svg` |
| Symbol Boolean | `codicon:symbol-boolean` | `https://api.iconify.design/codicon/symbol-boolean.svg` |
| Symbol Array | `codicon:symbol-array` | `https://api.iconify.design/codicon/symbol-array.svg` |
| Symbol Keyword | `codicon:symbol-keyword` | `https://api.iconify.design/codicon/symbol-keyword.svg` |
| Symbol Snippet | `codicon:symbol-snippet` | `https://api.iconify.design/codicon/symbol-snippet.svg` |
| Symbol Namespace | `codicon:symbol-namespace` | `https://api.iconify.design/codicon/symbol-namespace.svg` |
| Symbol Structure | `codicon:symbol-structure` | `https://api.iconify.design/codicon/symbol-structure.svg` |

### 11.6 通用 UI 概念

| 概念 | codicon 引用 | SVG URL |
|------|------------|---------|
| Check | `codicon:check` | `https://api.iconify.design/codicon/check.svg` |
| Close/Error | `codicon:error` | `https://api.iconify.design/codicon/error.svg` |
| Warning | `codicon:warning` | `https://api.iconify.design/codicon/warning.svg` |
| Info | `codicon:info` | `https://api.iconify.design/codicon/info.svg` |
| Add | `codicon:add` | `https://api.iconify.design/codicon/add.svg` |
| Delete/Trash | `codicon:trash` | `https://api.iconify.design/codicon/trash.svg` |
| Edit | `codicon:edit` | `https://api.iconify.design/codicon/edit.svg` |
| Refresh | `codicon:refresh` | `https://api.iconify.design/codicon/refresh.svg` |
| Lock | `codicon:lock` | `https://api.iconify.design/codicon/lock.svg` |
| Unlock | `codicon:unlock` | `https://api.iconify.design/codicon/unlock.svg` |
| Link | `codicon:link` | `https://api.iconify.design/codicon/link.svg` |
| External Link | `codicon:link-external` | `https://api.iconify.design/codicon/link-external.svg` |
| Globe | `codicon:globe` | `https://api.iconify.design/codicon/globe.svg` |
| Cloud | `codicon:cloud` | `https://api.iconify.design/codicon/cloud.svg` |
| Server | `codicon:server` | `https://api.iconify.design/codicon/server.svg` |
| Database | `codicon:database` | `https://api.iconify.design/codicon/database.svg` |
| Package | `codicon:package` | `https://api.iconify.design/codicon/package.svg` |
| Rocket/Deploy | `codicon:rocket` | `https://api.iconify.design/codicon/rocket.svg` |
| Bell/Notification | `codicon:bell` | `https://api.iconify.design/codicon/bell.svg` |
| Person | `codicon:person` | `https://api.iconify.design/codicon/person.svg` |
| Home | `codicon:home` | `https://api.iconify.design/codicon/home.svg` |
| Calendar | `codicon:calendar` | `https://api.iconify.design/codicon/calendar.svg` |
| Star | `codicon:star-full` | `https://api.iconify.design/codicon/star-full.svg` |
| Bookmark | `codicon:bookmark` | `https://api.iconify.design/codicon/bookmark.svg` |
| Tag | `codicon:tag` | `https://api.iconify.design/codicon/tag.svg` |
| Play | `codicon:play` | `https://api.iconify.design/codicon/play.svg` |
| Stop | `codicon:stop-circle` | `https://api.iconify.design/codicon/stop-circle.svg` |
| Shield | `codicon:shield` | `https://api.iconify.design/codicon/shield.svg` |
| Key | `codicon:key` | `https://api.iconify.design/codicon/key.svg` |
| Plug | `codicon:plug` | `https://api.iconify.design/codicon/plug.svg` |
| Lightbulb | `codicon:lightbulb` | `https://api.iconify.design/codicon/lightbulb.svg` |
| Heart | `codicon:heart` | `https://api.iconify.design/codicon/heart.svg` |
| Heart Filled | `codicon:heart-filled` | `https://api.iconify.design/codicon/heart-filled.svg` |
| Split Vertical | `codicon:split-vertical` | `https://api.iconify.design/codicon/split-vertical.svg` |
| Split Horizontal | `codicon:split-horizontal` | `https://api.iconify.design/codicon/split-horizontal.svg` |
| Browser | `codicon:browser` | `https://api.iconify.design/codicon/browser.svg` |
| Device Mobile | `codicon:device-mobile` | `https://api.iconify.design/codicon/device-mobile.svg` |

---

## 12. 文件类型图标 (vscode-icons)

VS Code 风格文件类型图标，共 1,513 个，命名规范统一为 `file-type-{name}`。适合需要文件类型语义的技术绘图（代码文件、配置文件、技术栈标识）。

### 12.1 编程语言

| 语言 | icon-pack 引用 | SVG URL |
|------|---------------|---------|
| Python | `vscode-icons:file-type-python` | `https://api.iconify.design/vscode-icons/file-type-python.svg` |
| JavaScript | `vscode-icons:file-type-js` | `https://api.iconify.design/vscode-icons/file-type-js.svg` |
| TypeScript | `vscode-icons:file-type-typescript` | `https://api.iconify.design/vscode-icons/file-type-typescript.svg` |
| Java | `vscode-icons:file-type-java` | `https://api.iconify.design/vscode-icons/file-type-java.svg` |
| Go | `vscode-icons:file-type-go` | `https://api.iconify.design/vscode-icons/file-type-go.svg` |
| Rust | `vscode-icons:file-type-rust` | `https://api.iconify.design/vscode-icons/file-type-rust.svg` |
| C | `vscode-icons:file-type-c` | `https://api.iconify.design/vscode-icons/file-type-c.svg` |
| C++ | `vscode-icons:file-type-cpp` | `https://api.iconify.design/vscode-icons/file-type-cpp.svg` |
| C# | `vscode-icons:file-type-csharp` | `https://api.iconify.design/vscode-icons/file-type-csharp.svg` |
| PHP | `vscode-icons:file-type-php` | `https://api.iconify.design/vscode-icons/file-type-php.svg` |
| Ruby | `vscode-icons:file-type-ruby` | `https://api.iconify.design/vscode-icons/file-type-ruby.svg` |
| Swift | `vscode-icons:file-type-swift` | `https://api.iconify.design/vscode-icons/file-type-swift.svg` |
| Kotlin | `vscode-icons:file-type-kotlin` | `https://api.iconify.design/vscode-icons/file-type-kotlin.svg` |
| Scala | `vscode-icons:file-type-scala` | `https://api.iconify.design/vscode-icons/file-type-scala.svg` |

### 12.2 前端框架与工具

| 框架/工具 | icon-pack 引用 | SVG URL |
|----------|---------------|---------|
| React | `vscode-icons:file-type-reactjs` | `https://api.iconify.design/vscode-icons/file-type-reactjs.svg` |
| Vue | `vscode-icons:file-type-vue` | `https://api.iconify.design/vscode-icons/file-type-vue.svg` |
| Angular | `vscode-icons:file-type-angular` | `https://api.iconify.design/vscode-icons/file-type-angular.svg` |
| Svelte | `vscode-icons:file-type-svelte` | `https://api.iconify.design/vscode-icons/file-type-svelte.svg` |
| Node.js | `vscode-icons:file-type-node` | `https://api.iconify.design/vscode-icons/file-type-node.svg` |
| NPM | `vscode-icons:file-type-npm` | `https://api.iconify.design/vscode-icons/file-type-npm.svg` |
| Webpack | `vscode-icons:file-type-webpack` | `https://api.iconify.design/vscode-icons/file-type-webpack.svg` |
| Vite | `vscode-icons:file-type-vite` | `https://api.iconify.design/vscode-icons/file-type-vite.svg` |

### 12.3 配置与标记文件

| 类型 | icon-pack 引用 | SVG URL |
|------|---------------|---------|
| HTML | `vscode-icons:file-type-html` | `https://api.iconify.design/vscode-icons/file-type-html.svg` |
| CSS | `vscode-icons:file-type-css` | `https://api.iconify.design/vscode-icons/file-type-css.svg` |
| SCSS | `vscode-icons:file-type-scss` | `https://api.iconify.design/vscode-icons/file-type-scss.svg` |
| JSON | `vscode-icons:file-type-json` | `https://api.iconify.design/vscode-icons/file-type-json.svg` |
| YAML | `vscode-icons:file-type-yaml` | `https://api.iconify.design/vscode-icons/file-type-yaml.svg` |
| XML | `vscode-icons:file-type-xml` | `https://api.iconify.design/vscode-icons/file-type-xml.svg` |
| Markdown | `vscode-icons:file-type-markdown` | `https://api.iconify.design/vscode-icons/file-type-markdown.svg` |
| SQL | `vscode-icons:file-type-sql` | `https://api.iconify.design/vscode-icons/file-type-sql.svg` |
| Shell | `vscode-icons:file-type-shell` | `https://api.iconify.design/vscode-icons/file-type-shell.svg` |

### 12.4 DevOps 与基础设施

| 工具 | icon-pack 引用 | SVG URL |
|------|---------------|---------|
| Docker | `vscode-icons:file-type-docker` | `https://api.iconify.design/vscode-icons/file-type-docker.svg` |
| Git | `vscode-icons:file-type-git` | `https://api.iconify.design/vscode-icons/file-type-git.svg` |
| Terraform | `vscode-icons:file-type-terraform` | `https://api.iconify.design/vscode-icons/file-type-terraform.svg` |
| Nginx | `vscode-icons:file-type-nginx` | `https://api.iconify.design/vscode-icons/file-type-nginx.svg` |
| MySQL | `vscode-icons:file-type-mysql` | `https://api.iconify.design/vscode-icons/file-type-mysql.svg` |
| SQLite | `vscode-icons:file-type-sqlite` | `https://api.iconify.design/vscode-icons/file-type-sqlite.svg` |
| MongoDB | `vscode-icons:file-type-mongo` | `https://api.iconify.design/vscode-icons/file-type-mongo.svg` |

> **注意**：Kubernetes、Linux、Redis 仅有 `folder-type-*` 图标（如 `vscode-icons:folder-type-kubernetes`），无 `file-type-` 变体；这几项优先改用 `logos`/`devicon` 等价图标。

---

## 图标包注册方法

注册 6 个图标包后，本目录中所有图标均可用 icon-pack 语法（`@{ icon: }` / `(pack:icon)`）引用；未注册时改用远程 URL 兜底（见上方「图标使用语法」）。CDN 链接裸用，不带版本号。

### CDN / mkdocs extra_javascript（推荐，无需打包器）

```javascript
(function () {
  function registerIcons() {
    if (typeof mermaid === 'undefined') { setTimeout(registerIcons, 100); return; }
    var iconPacks = ['logos', 'skill-icons', 'devicon', 'codicon', 'gcp', 'vscode-icons'];
    try {
      mermaid.registerIconPacks(iconPacks.map(function (name) {
        return { name: name, loader: function () {
          return fetch('https://unpkg.com/@iconify-json/' + name + '/icons.json').then(function (res) { return res.json(); });
        }};
      }));
    } catch (e) { console.warn('Icon pack registration failed:', e.message); }
  }
  registerIcons();
})();
```

### 多 icon set 注册（自托管/Webpack/Vite）

```javascript
import mermaid from 'mermaid';

mermaid.registerIconPacks([
  { name: 'logos',        loader: () => fetch('https://unpkg.com/@iconify-json/logos/icons.json').then(res => res.json()) },
  { name: 'skill-icons',  loader: () => fetch('https://unpkg.com/@iconify-json/skill-icons/icons.json').then(res => res.json()) },
  { name: 'devicon',      loader: () => fetch('https://unpkg.com/@iconify-json/devicon/icons.json').then(res => res.json()) },
  { name: 'codicon',      loader: () => fetch('https://unpkg.com/@iconify-json/codicon/icons.json').then(res => res.json()) },
  { name: 'gcp',          loader: () => fetch('https://unpkg.com/@iconify-json/gcp/icons.json').then(res => res.json()) },
  { name: 'vscode-icons', loader: () => fetch('https://unpkg.com/@iconify-json/vscode-icons/icons.json').then(res => res.json()) },
]);

mermaid.initialize({ startOnLoad: true });
```

### npm 安装

```bash
npm install @iconify-json/logos @iconify-json/skill-icons @iconify-json/devicon @iconify-json/codicon @iconify-json/gcp @iconify-json/vscode-icons
```

```javascript
mermaid.registerIconPacks([
  { name: 'logos',        loader: () => import('@iconify-json/logos').then(m => m.icons) },
  { name: 'skill-icons',  loader: () => import('@iconify-json/skill-icons').then(m => m.icons) },
  { name: 'devicon',      loader: () => import('@iconify-json/devicon').then(m => m.icons) },
  { name: 'codicon',      loader: () => import('@iconify-json/codicon').then(m => m.icons) },
  { name: 'gcp',          loader: () => import('@iconify-json/gcp').then(m => m.icons) },
  { name: 'vscode-icons', loader: () => import('@iconify-json/vscode-icons').then(m => m.icons) },
]);
```

---

## 🛠 Iconify API 搜索

当需要查找不在本目录中的图标时：

```
GET https://api.iconify.design/search?query={关键词}&limit=20&prefixes=logos,devicon,gcp,vscode-icons,codicon,skill-icons
```

响应格式：`{"icons": ["logos:aws-ec2", "devicon:docker", ...], "total": 5, ...}`

常用组合：
- 云服务图标：`prefixes=logos`
- Google Cloud 服务：`prefixes=gcp`
- 编程语言/框架/工具：`prefixes=devicon,skill-icons`
- 文件类型图标：`prefixes=vscode-icons`
- 开发概念/IDE：`prefixes=codicon`
- 全面搜索：`prefixes=logos,devicon,gcp,vscode-icons,codicon,skill-icons`

> **重要提示**: 搜索结果返回的是 `pack:icon-name` 格式。已注册图标包时直接用该格式；未注册时 SVG URL 需转换为 `https://api.iconify.design/{pack}/{icon-name}.svg`。

## Icon Catalog
 
The quick-reference catalog for all icons available in Mermaid diagrams. Built on the unified [Iconify](https://iconify.design/) icon system, with 6 curated icon sets for full technical-drawing coverage.
 
This is the **single source of truth** for icon-pack registration and icon references. Do not duplicate the registration snippet in other files — reference this one instead.
 
### Icon sets at a glance
 
| Icon set | Prefix | Count | Palette | Purpose | When to use |
|----------|--------|-------|---------|---------|-------------|
| **logos** | `logos` | 1,861 | Yes | Product / cloud-service logos | Cloud vendors, SaaS, open-source project logos |
| **devicon** | `devicon` | 1,036 | Yes | Languages / tools / frameworks | Tech-stack icons; widest coverage |
| **gcp** | `gcp` | 214 | Yes | Google Cloud service icons | Dedicated icons for each GCP service |
| **vscode-icons** | `vscode-icons` | 1,513 | Yes | File-type icons | File / tech-stack file-type icons; consistent naming |
| **codicon** | `codicon` | 602 | No | IDE / dev-operation concepts | Git, terminal, debug, file operations |
| **skill-icons** | `skill-icons` | 400 | Yes | Programming-skill icons | When light/dark theme variants are needed |
 
### Icon lookup decision tree
 
When drawing diagrams, choose an icon set by this priority:
 
```
Need a cloud-service / product logo?
├── Google Cloud service icon? → gcp (most complete, 214 dedicated service icons)
├── Other cloud service / product → logos (preferred) or devicon
└── Need a language / framework / tool?
    ├── Need a file-type icon (file-type-python, file-type-docker)? → vscode-icons (consistent naming, 1,513 icons)
    ├── Other tech stack → devicon (preferred) or skill-icons
    └── Need an IDE / dev-operation concept (Git, Terminal, Debug)?
        ├── Yes → codicon
        └── Unsure → search: https://api.iconify.design/search?query={keyword}&prefixes=logos,devicon,gcp,vscode-icons,codicon,skill-icons
 
Prohibited — emoji: emoji is strictly prohibited in all diagrams. Always use the icons in this catalog or semantic coloring to convey meaning.
```
 
### Icon syntax (by registration state)
 
**Core decision rule**: choose syntax by whether the render environment has registered icon packs. **Do not mix the two syntaxes in one diagram.**
 
**Icon packs registered** → use icon-pack syntax (recommended):
```
%% flowchart
NodeName@{ icon: "logos:aws-ec2", form: "square", label: "EC2", pos: "b", h: 48 }
 
%% architecture-beta
service ec2(logos:aws-ec2)[EC2]
```
 
**Icon packs NOT registered** → use remote-URL fallback (works in every environment):
```
NodeName@{ img: "https://api.iconify.design/logos/aws-ec2.svg", label: "EC2", pos: "b", h: 48, constraint: "on" }
```
 
**API URL pattern** (for the remote fallback):
```
https://api.iconify.design/{prefix}/{icon-name}.svg
```
 
> **Anti-distortion rule**: set only `h`, enable `constraint: "on"`; never set both `w` and `h` simultaneously.
 
---
 
## 1. Cloud Providers
 
### 1.1 AWS
 
| Service | icon-pack reference | SVG URL | Aspect ratio |
|---------|---------------------|---------|--------------|
| AWS (generic) | `logos:aws` | `https://api.iconify.design/logos/aws.svg` | — |
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
 
The `gcp` set provides 214 dedicated GCP service icons with the most complete naming; `logos`/`devicon` only offer generic cloud icons.
 
**`gcp:` service icons** (recommended for GCP service-level icons):
 
| Service | icon-pack reference | SVG URL |
|---------|---------------------|---------|
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
 
**`logos:` / `devicon:` generic cloud icons**:
 
| Service | icon-pack reference | SVG URL | Aspect ratio |
|---------|---------------------|---------|--------------|
| Google Cloud (generic) | `logos:google-cloud` | `https://api.iconify.design/logos/google-cloud.svg` | 1:1 |
| Cloud Functions | `logos:google-cloud-functions` | `https://api.iconify.design/logos/google-cloud-functions.svg` | 1:1 |
| Cloud Run | `logos:google-cloud-run` | `https://api.iconify.design/logos/google-cloud-run.svg` | 1:1 |
| Google Cloud (devicon) | `devicon:googlecloud` | `https://api.iconify.design/devicon/googlecloud.svg` | 1:1 |
 
### 1.3 Azure
 
| Service | icon-pack reference | SVG URL | Aspect ratio |
|---------|---------------------|---------|--------------|
| Azure (generic) | `logos:microsoft-azure` | `https://api.iconify.design/logos/microsoft-azure.svg` | 1:1 |
| Azure (devicon) | `devicon:azure` | `https://api.iconify.design/devicon/azure.svg` | 1:1 |
| Azure DevOps | `devicon:azuredevops` | `https://api.iconify.design/devicon/azuredevops.svg` | 1:1 |
| Azure Data Factory | `devicon:azuredatafactory` | `https://api.iconify.design/devicon/azuredatafactory.svg` | 1:1 |
| Azure SQL Database | `devicon:azuresqldatabase` | `https://api.iconify.design/devicon/azuresqldatabase.svg` | 1:1 |
 
### 1.4 Other cloud platforms
 
| Platform | icon-pack reference | SVG URL |
|----------|---------------------|---------|
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
| IPFS | `logos:ipfs` | `https://api.iconify.design/logos/ipfs.svg` (non-square) |
 
> **Note**: `logos:ipfs` has an aspect ratio of ~3:1 (severely horizontal); never set both `w` and `h` simultaneously.
 
---
 
## 2. Programming Languages
 
Use **devicon** (preferred, cleanest naming) or **skill-icons** (has light/dark variants).
 
| Language | devicon (preferred) | skill-icons | logos |
|----------|---------------------|-------------|-------|
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
 
**SVG URL examples** (devicon):
```
https://api.iconify.design/devicon/python.svg
https://api.iconify.design/devicon/go.svg
https://api.iconify.design/devicon/rust.svg
```
 
---
 
## 3. Runtimes & Backend Frameworks
 
| Technology | devicon (preferred) | skill-icons | logos |
|------------|---------------------|-------------|-------|
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
 
## 4. Databases & Storage
 
| Database | devicon (preferred) | skill-icons | logos |
|----------|---------------------|-------------|-------|
| PostgreSQL | `devicon:postgresql` | `skill-icons:postgresql-light` / `postgresql-dark` | `logos:postgresql` |
| MySQL | `devicon:mysql` | `skill-icons:mysql-light` / `mysql-dark` | `logos:mysql-icon` |
| MongoDB | `devicon:mongodb` | `skill-icons:mongodb` | `logos:mongodb-icon` |
| Redis | `devicon:redis` | `skill-icons:redis-light` / `redis-dark` | `logos:redis` (non-square) |
| SQLite | `devicon:sqlite` | `skill-icons:sqlite` | `logos:sqlite` |
| MariaDB | `devicon:mariadb` | — | `logos:mariadb-icon` |
| Cassandra | `devicon:cassandra` | `skill-icons:cassandra-light` / `cassandra-dark` | `logos:cassandra` |
| Neo4j | `devicon:neo4j` | — | `logos:neo4j` |
| Elasticsearch | `devicon:elasticsearch` | `skill-icons:elasticsearch-light` / `elasticsearch-dark` | `logos:elasticsearch` |
| InfluxDB | `devicon:influxdb` | — | `logos:influxdb-icon` |
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
 
> **Note**: `logos:redis` has an aspect ratio of ~3.2:1; never set both `w` and `h` in `@{ img: }`. Alternatives: `logos:heroku-redis` (more square) or `devicon:redis` (1:1).
 
---
 
## 5. DevOps & CI/CD
 
### 5.1 CI/CD platforms
 
| Tool | devicon (preferred) | skill-icons | logos |
|------|---------------------|-------------|-------|
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
 
### 5.2 Infrastructure as Code (IaC)
 
| Tool | devicon (preferred) | skill-icons | logos |
|------|---------------------|-------------|-------|
| Terraform | `devicon:terraform` | `skill-icons:terraform-light` / `terraform-dark` | `logos:terraform-icon` |
| Ansible | `devicon:ansible` | `skill-icons:ansible` | `logos:ansible` |
| Pulumi | `devicon:pulumi` | — | `logos:pulumi` |
| Chef | — | — | `logos:chef` |
| Puppet | — | — | `logos:puppet-icon` |
| Vagrant | `devicon:vagrant` | — | `logos:vagrant-icon` |
| Packer | `devicon:packer` | — | `logos:packer` |
| OpenTofu | — | — | `logos:opentofu` |
| Crossplane | — | — | `logos:crossplane` |
 
### 5.3 Containers & orchestration
 
| Tool | devicon (preferred) | skill-icons | logos |
|------|---------------------|-------------|-------|
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
 
---
 
## 6. Observability
 
| Tool | devicon (preferred) | skill-icons | logos |
|------|---------------------|-------------|-------|
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
 
## 7. Messaging & Streaming
 
| Service | devicon (preferred) | skill-icons | logos |
|---------|---------------------|-------------|-------|
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
 
| Technology | devicon (preferred) | skill-icons | logos |
|------------|---------------------|-------------|-------|
| OpenAI | — | — | `logos:openai-icon` |
| Anthropic | — | — | `logos:anthropic-icon` |
| TensorFlow | `devicon:tensorflow` | `skill-icons:tensorflow-light` / `tensorflow-dark` | `logos:tensorflow` |
| PyTorch | `devicon:pytorch` | `skill-icons:pytorch-light` / `pytorch-dark` | `logos:pytorch-icon` |
 
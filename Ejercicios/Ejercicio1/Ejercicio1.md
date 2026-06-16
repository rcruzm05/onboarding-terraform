# 🧪 Ejercicio 1 — Crear un bucket en GCP con Terraform CLI

Este ejercicio introduce los conceptos básicos de **Terraform** mediante la creación de un recurso sencillo en **Google Cloud Platform (GCP)**: un bucket de **Cloud Storage**.

La intención es que aprendas el flujo básico de Terraform CLI ejecutando los comandos desde tu máquina local.

---

# 🎯 Objetivo

Crear un **bucket de Cloud Storage** en GCP usando Terraform CLI.

Al finalizar el ejercicio deberás haber:

* Creado una estructura básica de archivos Terraform.
* Configurado el provider de Google Cloud.
* Declarado un recurso `google_storage_bucket`.
* Usado variables para parametrizar el proyecto, nombre y ubicación del bucket.
* Ejecutado el flujo básico de Terraform CLI.
* Validado la creación del bucket en GCP.
* Eliminado la infraestructura creada.

---

# 🧠 Conceptos que practicarás

Durante este ejercicio practicarás los siguientes conceptos:

| Concepto           | Descripción                                                                      |
| ------------------ | -------------------------------------------------------------------------------- |
| Provider           | Plugin que permite a Terraform interactuar con una plataforma, en este caso GCP. |
| Resource           | Bloque que representa infraestructura que Terraform debe crear o administrar.    |
| Variable           | Valor parametrizable que permite reutilizar el código.                           |
| `terraform.tfvars` | Archivo usado para asignar valores a las variables.                              |
| State              | Archivo donde Terraform guarda el estado de los recursos administrados.          |
| Plan               | Vista previa de los cambios que Terraform realizará.                             |
| Apply              | Ejecución real de los cambios definidos en el código.                            |
| Destroy            | Eliminación de la infraestructura administrada por Terraform.                    |

---

# 📂 Paso 1 — Crear la estructura de archivos

Dentro del repositorio, entra al directorio `Ejercicios`:

```bash
cd Ejercicios
```

Crea un directorio para el ejercicio:

```bash
mkdir Ejercicio1
cd Ejercicio1
```

Dentro del directorio `Ejercicio1`, crea los siguientes archivos:

```text
Ejercicios/
└── Ejercicio1/
    ├── versions.tf
    ├── provider.tf
    ├── main.tf
    ├── variables.tf
    ├── terraform.tfvars
    └── outputs.tf
```

---

# 📄 Paso 2 — Configurar versiones en `versions.tf`

El archivo `versions.tf` define la versión mínima de Terraform y los providers requeridos.

---

# 📄 Paso 3 — Configurar el provider en `provider.tf`

El archivo `provider.tf` define cómo Terraform se conectará a GCP.

---

# 📄 Paso 4 — Definir variables en `variables.tf`

El archivo `variables.tf` contiene las variables que usará el código Terraform.

---

# 📄 Paso 5 — Asignar valores en `terraform.tfvars`

El archivo `terraform.tfvars` permite asignar valores a las variables.

Agrega un contenido similar al siguiente:

```hcl
project_id      = "sit-devops-training"
bucket_name     = "tf-onboarding-nombre-usuario-001"
bucket_location = "us-central1"
```

Modifica `bucket_name` usando tu nombre de usuario o algún identificador personal.

Ejemplo:

```hcl
bucket_name = "tf-onboarding-rcruzm05-001"
```

> El nombre del bucket debe ser único globalmente en GCP. Si el nombre ya existe, Terraform mostrará un error al intentar crearlo.

---

# 📄 Paso 6 — Crear el recurso en `main.tf`

El archivo `main.tf` contendrá la definición del bucket.

---

# 🔐 Paso 7 — Validar autenticación con GCP

Antes de ejecutar Terraform, valida que tienes una cuenta autenticada con `gcloud`:

```bash
gcloud auth list
```

Valida el proyecto activo:

```bash
gcloud config get-value project
```

Si necesitas configurar el proyecto, ejecuta:

```bash
gcloud config set project sit-devops-training
```

Si aún no tienes credenciales de aplicación configuradas, puedes ejecutar:

```bash
gcloud auth application-default login
```

> Terraform puede usar Application Default Credentials para autenticarse contra GCP desde tu entorno local.

---

# 🚀 Paso 8 — Inicializar Terraform

Ejecuta:

```bash
terraform init
```

Este comando inicializa el directorio de trabajo y descarga el provider de Google.

Resultado esperado:

```text
Terraform has been successfully initialized!
```

---

# 🧹 Paso 9 — Formatear archivos Terraform

Ejecuta:

```bash
terraform fmt
```

Este comando aplica el formato estándar de Terraform a los archivos `.tf`.

También puedes validar el formato sin modificar archivos:

```bash
terraform fmt -check
```

---

# ✅ Paso 10 — Validar la configuración

Ejecuta:

```bash
terraform validate
```

Este comando valida que la configuración sea sintácticamente correcta.

Resultado esperado:

```text
Success! The configuration is valid.
```

---

# 🔎 Paso 11 — Revisar el plan

Ejecuta:

```bash
terraform plan
```

Terraform mostrará los cambios que realizará.

Resultado esperado:

```text
Plan: 1 to add, 0 to change, 0 to destroy.
```

Antes de continuar, revisa que el recurso a crear sea el bucket esperado.

---

# 🏗️ Paso 12 — Aplicar los cambios

Ejecuta:

```bash
terraform apply
```

Terraform mostrará nuevamente el plan y pedirá confirmación.

Escribe:

```text
yes
```

Al finalizar, Terraform mostrará los outputs configurados.

---

# 🔍 Paso 13 — Validar el bucket creado

Puedes validar el bucket desde la consola de GCP o usando `gcloud`:

```bash
gcloud storage buckets list --project sit-devops-training
```

También puedes buscar directamente el nombre del bucket:

```bash
gcloud storage buckets list --project sit-devops-training | grep tf-onboarding
```

---

# 📦 Paso 14 — Revisar el state local

Después del `apply`, Terraform generará archivos de estado en tu directorio local.

Puedes listar los archivos:

```bash
ls -la
```

Deberías ver archivos como:

```text
terraform.tfstate
.terraform/
.terraform.lock.hcl
```

El archivo `terraform.tfstate` contiene el estado de la infraestructura administrada por Terraform.

> Para este ejercicio básico, el state se mantiene localmente. En escenarios colaborativos se recomienda usar un backend remoto o una plataforma como HCP Terraform.

---

# 🧨 Paso 15 — Destruir la infraestructura

Cuando termines el ejercicio, elimina el bucket para evitar costos o recursos innecesarios:

```bash
terraform destroy
```

Terraform pedirá confirmación.

Escribe:

```text
yes
```

---

# 🔍 Paso 16 — Validar eliminación del bucket

Ejecuta nuevamente:

```bash
gcloud storage buckets list --project sit-devops-training
```

Confirma que el bucket creado ya no aparezca.

---

# ✅ Resultado esperado

Al finalizar este ejercicio, deberás haber logrado lo siguiente:

* Crear una estructura básica de archivos Terraform.
* Configurar el provider de Google Cloud.
* Definir variables de entrada.
* Asignar valores usando `terraform.tfvars`.
* Declarar un bucket de Cloud Storage.
* Ejecutar `terraform init`.
* Ejecutar `terraform fmt`.
* Ejecutar `terraform validate`.
* Ejecutar `terraform plan`.
* Ejecutar `terraform apply`.
* Validar el recurso creado en GCP.
* Revisar el state local.
* Ejecutar `terraform destroy`.
* Confirmar la eliminación del recurso.

---

# ⚠️ Nota importante

Este ejercicio crea infraestructura real en GCP.

Recuerda destruir los recursos al finalizar:

```bash
terraform destroy
```

No subas credenciales, llaves JSON ni información sensible al repositorio.


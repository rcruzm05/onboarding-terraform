# 🧪 Ejercicios de Terraform en GCP

Este repositorio contiene ejercicios prácticos para aprender **Infraestructura como Código (IaC)** usando **Terraform** y **Google Cloud Platform (GCP)**.

---

# 📂 Estructura del repositorio

```text
.
├── README.md
└── Ejercicios/
    ├── Ejercicio1.md
    └── EjercicioN.md
```

---

# 📘 Lista de ejercicios

## Ejercicio 1 — Crear un bucket en GCP usando Terraform

En este ejercicio crearás un **bucket de Cloud Storage** utilizando Terraform.

Aprenderás:

* Qué es un provider
* Qué es un resource
* Cómo ejecutar `terraform init`
* Cómo ejecutar `terraform plan`
* Cómo ejecutar `terraform apply`
* Cómo eliminar infraestructura con `terraform destroy`

---

# 🌿 Flujo de trabajo con ramas

La rama `terraform-basico` contiene las instrucciones base del ejercicio.

Cada participante deberá crear una rama individual a partir de `terraform-basico` usando el siguiente formato:

```bash
git checkout -b terraform-basico-nombre-usuario
```

Ejemplo:

```bash
git checkout -b terraform-basico-rcruzm05
```

El flujo recomendado es:

Después de realizar los cambios del ejercicio, se deberán subir a la rama individual:

```bash
git add .
git commit -m "docs: resolver ejercicio básico de Terraform"
git push -u origin terraform-basico-nombre-usuario
```

Ejemplo:

```bash
git push -u origin terraform-basico-rcruzm05
```

---

# 🧠 Requisitos

Antes de comenzar, debes tener:

* Terraform instalado
* Google Cloud SDK (`gcloud`) instalado
* Acceso a proyecto sit-devops-training

Verifica Terraform:

```bash
terraform version
```

Verifica gcloud:

```bash
gcloud version
```

---

# ⚠️ Nota importante

Este repositorio crea **infraestructura real en GCP**.

Recuerda eliminar los recursos cuando termines para evitar costos:

```bash
terraform destroy
```


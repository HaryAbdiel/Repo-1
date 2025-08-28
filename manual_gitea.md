#Guía para trabajar con Gitea (Modelab)
Este manual explica cómo crear un repositorio local y subirlo a **Modelab (Gitea)** usando **HTTPS +
Token**.
---
## **1. Preparación inicial**
1. Instalar **Git** en su computadora.
2. Instalar **Git LFS**:
git lfs install
3. Configurar su nombre y correo (solo la primera vez):
git config --global user.name "Tu Nombre"
git config --global user.email "tu@correo.com"
---
## **2. Cuenta en Modelab**
1. El administrador les dará un **usuario y contraseña temporal**.
2. Entrar en: http://189.240.222.211:3000/
3. Cambiar la contraseña en el primer 
inicio.
---
## **3. Crear un Token personal**
1. Ir a Profile → Settings → Applications → Generate Token.
2. Nombre sugerido: laptop.
3. Permisos mínimos:
Repository → Read and Write
All (public, private, limited)
4. Clic en Generate Token → copiar y guardar el token (■■ aparece solo una vez).
Guardar el token en Git para no escribirlo cada vez:
git config --global credential.helper store
---
## **4. Crear un repositorio local**
1. En su computadora:
mkdir mi-proyecto
cd mi-proyecto
git init
git lfs install
2. Agregar archivos y primer commit:
echo "# Mi Proyecto" > README.md
git add .
git commit -m "Primer commit"
---
## **5. Crear el repositorio vacío en Modelab**
- En la web de Gitea → clic en + → New Repository.
- Nombre: mi-proyecto.
- **No marcar** Initialize with README 
(ya lo tienes local).
---
## **6. Conectar el repositorio**   

### **6.1 Conectar el repositorio local a gitea**  
git remote add modelab http://189.240.222.211:3000//mi-proyecto.git

### **6.2 Conectar gitea con el repositorio local**
Nota: este paso se hace cuando queremos enlazar el gitea a la memoria local, es decir un repositorio ya existente 

git clone http://189.240.222.211:3000//mi-proyecto.git
git remote add modelab http://189.240.222.211:3000//mi-proyecto.git 
---
## **7. Subir el repositorio a Modelab**
git branch -M main
git push -u modelab main
Cuando pida credenciales:
- Username → su usuario en Gitea
- Password → el token personal
---
## **8. Archivos grandes con Git LFS**
Antes de subir archivos grandes:
git lfs track "*.nc" "*.tif" "*.zip" "*.mat"
git add .gitattributes
git commit -m "Habilitar LFS"
git push
---
## **9. Limpieza (opcional)**
Si en algún momento ya no necesitan usar Modelab en ese proyecto:
git remote remove modelab
---
Recomendaciones
- **No compartas tu token.**
- Si lo pierdes, genera uno nuevo en Settings → Applications.
- Usa mensajes de commit claros y descriptivos.
- Siempre sincroniza tus cambios con git push.
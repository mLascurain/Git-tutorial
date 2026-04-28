
 # 🚀 Git Tutorial: De 0% a 100% en un solo lugar 💯

Armé este repo para explicar qué onda Git, para qué sirve, cómo laburo yo e inclusive abordamos conceptos avanzados a medida que vamos avanzando. <br>La idea es que si no cazás una de Git, con esto salgas jugando y tengas fundamentos solidos.
 
> Fuentes:<br>
> Utilice el libro de [Pro Git](https://git-scm.com/book/es/v2) y la [documentacion oficial de Git](https://git-scm.com/docs) para poder armar este tutorial. 
> Recomiendo que si queres seguir estudiando mas a fondo sobre Git y Github, le pegues un ojo a estas fuentes que son buenisimas.

> Si tienen sugerencias de como mejorar este README ayudaria un monton. Una estrella en el repo se agradece 😉

---

### 1~ ¿Qué es Git y por qué es clave? 🗝️

Imaginate que estás codeando sin Git, si te mandás una moco, perdés todo o terminás con archivos tipo: `app_FINAL_esta_si_v3_PROMETO_(1).zip`. Lo tenes que pedir.

**Git es como el sistema de checkpoints de un juegito:**
*   **Sirve para:** Sacar "fotos" (snapshots) del proyecto.
*   **Permite:** Viajar en el tiempo si rompes algo _(pasa seguido)_ y laburar con otros sin que se pisen los cambios.

  _(antes de poder usarlo lo vas a tener que instalar, googlea no es dificil)_

 --> Arrancas git en tu proyecto con `git init`

---

### 2~ Como usar git: Add y Commit 📚

Antes de arrancar a usarlo tenes que conocer los tres estados en git:

- Working Directory: Es la carpeta en tu computadora donde editas, creas o borras archivos. 
  Cuando cambias un archivo pero todavia no le avisaste a Git que lo tenga en cuenta, se encuentra en este estado ("modificado" o modified).

- Staging Area: Es una carpeta invisible donde colocas los cambios que quieres incluir en el próximo commit. 
  Podes stagear tus cambios usando `git add`, y para ver que cambios estan stageados o faltan por stagear usas `git status`.

- Git Directory: Es donde Git almacena la base de datos de los cambios (el historial). 
  Cuando haces `git commit`, los archivos preparados pasan del staging area a guardarse definitivamente como una foto (snapshot).

  _En un toque vamos a ver los comandos en profundidad_

---

### 3~ Conceptos que tenés que conocer sí o sí 👀
#### _(lo que esta con signo de exclamacion lo vamos a volver a ver mas adelante, no te hagas la cabeza si no lo cazas de una)_

*   **Local:** Tu compu.
*   **Repo (Repositorio):** Es la carpeta del proyecto que Git está vigilando.
*   **Commit (`*`):** Una foto de tus archivos en un momento exacto. Cada commit se le tiene que poner un nombre para saber qué corno hiceste.
*   !**Remote (u "Origin"):** Es la copia que vive en la nube.
*   !**Rama (Branch):** Un camino aparte, como una difurcacion del codigo. Te poes abrir una rama para probar algo sin romper la versión principal que ya funciona.
*   !**HEAD:** Es un puntero que indica la rama o commit actual en el que estás trabajando. Sirve para saber dónde estas en el historial, y usualmente apunta al último commit realizado en tu rama activa.

---

Antes de poder sacarle una "foto" a tu projecto, tenes que hacer esto.

1. **`git add <archivo>` (guardas los archivos):** 
   Acá elegís qué archivos querés guardar. 
   * *Estado:* **Staging**. Los archivos están "en espera".
> [!TIP]
> ### Como agregar varios archivos al stage:
> Podes usar "`git add .`" en lugar del nombre de los archivos para guardar todos los archivos modificados del repo
> <br>Y si te arrepentis podes tirar `git reset` para sacar los archivos del staging area

2. **`git commit -m "descripción"`:** 
   Acá confirmás que lo que está guardado, le sacas la "foto". 
   * *Estado:* **Committed**. El cambio ya es parte de la historia oficial en tu PC.

Y ahora tenes tu nueva "foto" ___(correctamente llamado commit)___ de tu proyecto

> [!note]
> ### Commit Rollback:
> Si queres volver a algun commit antiguo podes usar `git log --oneline` para ver la lista de commits
> Y despues `git reset --hard <commit-hash>` para hacer el rollback hacia ese commit

---

### 4~ Diferencias Git vs GitHub... 🧩


| Aspecto | Git | GitHub |
| :--- | :--- | :--- |
| **Qué es** | Herramienta de control de versiones | Plataforma para alojar repositorios Git |
| **Dónde funciona** | Local (tu computadora) | Remoto (en la nube) |
| **Para qué sirve** | Gestionar cambios y versiones | Compartir y colaborar en proyectos |
| **Instalación** | En tu computadora personal. | No requiere (se usa en el navegador). |


---

> [!note]
> ### Configuracion:
> Para poder subir tu proyecto a github tenes que configurar tu terminal para que tengas acceso a tu cuenta de GitHub
> Si estas en windows podes usar winget para instalar el [CLI de Github](https://github.com/cli/cli/blob/trunk/docs/install_windows.md#winget)
> Una vez instalado podes hacer `gh auth login` y seguir los pasos, eligiendo HTTPS como protocolo y logeandote desde el browser.

> [!note]
> ### SSH Auth _(Recomendado)_
> Si preferis una opcion mas segura podes optar por configurarlo con una clave de ssh _(este paso a paso funciona para linux/wsl pero lo podes activar en cualquier OS)_.
> Generala con este comando `ssh-keygen -t ed25519 -C "tu-mail@tu-mail.com"` 
> Arrancas tu agente de ssh y lo agregas con `eval "$(ssh-agent -s)"` y despues `ssh-add ~/.ssh/id_ed25519`
> Una vez que hiciste eso, copia tu clave publica con `cat ~/.ssh/id_ed25519.pub` y agregala en tus [Settings de GitHub](https://github.com/settings/keys)

---

### 5~ Como conectar tu repo local con GitHub 🌐

1.  Para poder subir tu repo a GitHub tenes que Crear un repositorio en la web y linkiarlo a tu repo local con:
  -> `git remote add origin "el link de tu origen"`

2.  Una vez hiciste eso poder pushear tus cambios commiteados al remote haciendo: `git push origin main` 
  - Esto sube tus cambios a la branch main _(en un toque vemos que es una branch)_

<img width="552" height="345" alt="create-repo" src="https://github.com/user-attachments/assets/db81a56f-b649-4c9b-82cd-dde9582f8169" />

> [!IMPORTANT]
> ### Esto es clave:
> El verdadero poder de Git entra cuando lo laburas junto a GitHub _(Hay otras alternativas como GitLab, Bitbucket entre otros)_. 
> Ademas es fundamental cuando lo laburas con otros en tu equipo

---

### 6~ Los comandos que se usan para sincronizar _(utiles si trabajas con mas personas en un repo)_ 


| Comando | Qué hace? | Toca mis archivos? |
| :--- | :--- | :--- |
| `git fetch` | Se trae las novedades del origin pero las guarda en una carpeta "invisible". | **NO modifica tus archivos**. Es super seguro. |
| `git merge` | Agarra los cambios de otra rama y los pega en la mía a la fuerza. | **SÍ**. Crea un commit de unión que a veces ensucia el historial. |
| `git pull` | Es el vago: hace un `fetch` y un `merge` todo de una. | **SÍ**. Es cómodo pero te puede saltar un quilombo de golpe. |
| `git rebase` | Mueve mis cambios para que parezca que los hice "después" de lo último del servidor. | **SÍ**. Deja el historial prolijo, como una línea recta. |


---

### 7~ Cómo se lee el historial (El dibujito de las ramas) 🪵

Git muestra el historial como un **grafo** (un mapa de estaciones).

```
(Lo último que se hizo)
  *   7a2b3c4 (HEAD -> main) El "Merge": acá se une todo.
  |\  
  | * 5e6f7g8 (rama-nueva) Antes de mergiar nos tenemos que traer los ultimos cambios de main
  | * 3h4i5j6 cambiamos los colores a un botón.
  | |
  * 1k2l3m4 Un compañero arregló un bug en la rama principal (main o master tipicamente).
  | |
  | |
  |/  
  * 9n0o1p2 El commit base.
(El pasado)
```

**¿Cómo se lee?**
*   **De abajo para arriba:** Lo viejo abajo, lo nuevo arriba.
*   **Las ramitas (`|/`):** Alguien se abrió para hacer algo distinto.
*   **Los cruces (`|\`):** Volvimos a juntar los caminos.

---

### 8~ Git Stash 📦

#### Algo que te puede pasar es que estes laburando en una funcionalidad, con todo el código por la mitad y de repente te tenes que poner a laburar en otra cosa mas urgente

> - No querés hacer un commit porque el código está roto o incompleto. Ahí es donde entra el **`git stash`**. 
>   Hacés lo urgente, y después seguis con lo que estabas laburando.

#### Cómo se usa?

1. **`git stash`** (O `git stash save "mensaje"`)
   * Agarrás todos tus cambios que no guardaste (los que están en `add` o sueltos) y los guardás en una pila secreta.
   * Tu rama queda **limpia**, como si no hubieras tocado nada. Ahora sí podés cambiar de rama y arreglar el bug urgente.

2. **`git stash list`**
   * Te muestra todos los stash que hiciste.

3. **`git stash pop`**
   * Es el que más vas a usar. Saca lo último que guardaste en el stash y lo vuelve a poner en tu código. **Ojo:** una vez que lo hacés, lo borra de la lista.

4. **`git stash apply`**
   * Igual que el `pop`, pero deja una copia en la lista por las dudas.

5. **`git stash drop`**
   * Si al final decidiste que lo que habías guardado en el stash era malardo y no lo querés más, con esto lo borrás al carajo.

---

### Ejemplo de uso real:
- Estás programando un botón: `index.html` modificado.
- *"Hay un error en el formulario de login!"*: **No podés cambiar de rama porque Git no te deja si tenés cambios sin guardar.**
- Tirás un **`git stash`**.
- Te vas a la rama del error _(o creas una para el hotfix)_, lo arreglás, hacés el push.
- Volvés a tu rama y tirás **`git stash pop`**.
- ¡Magia! El código del botón vuelve a aparecer y seguís como si nada.

---

### 9~ Mi Workflow Profesional (El paso a paso "Limpio") ✨

Para que el historial no sea un bardo y quede cheto, yo sigo este orden:

#### Paso A: Preparo mis cambios
1.  `git add .` (Meto los cambios en el stage).
2.  `git commit -m "feat: agregué el login"`

#### Paso B: Me fijo qué hicieron los demás (Sincronización)
3.  **`git fetch origin`**
    *(Me bajo lo que hicieron los pibes mientras yo estaba en la mía).*
4.  **`git diff HEAD..origin/main`**
    *(Clave: comparo mi código con el de ellos. Si veo que tocamos lo mismo, ya me mentalizo que se viene un conflicto).*
5.  **`git rebase origin/main`**
    *(Git saca mis commits, pone lo nuevo de los demás y después pega mis cambios arriba. Queda una línea recta hermosa!)*

#### Paso C: Si salta un conflicto (No entres en pánico)
Si el rebase se traba:
1.  Abro el archivo que llora y elijo qué código queda.
2.  `git add <archivo_arreglado>`.
3.  `git rebase --continue` (Listo! Seguimos camino).
*Si se fue todo al pasto y no sabés qué hiciste: `git rebase --abort` y lo ves despues cuando te de el bocho.*

#### Paso D: Lo subo
6.  **`git push origin mi-rama`**

---

> [!CAUTION]
> ### IMPORTANTE SOBRE EL USO DE REBASE
> **NUNCA hagas rebase en ramas publicas.**
> El rebase "reescribe la historia". Si vos ya subiste algo y después le hacés un rebase, le vas a romper la cabeza a tus compañeros cuando quieran bajar tus cambios. 
> Hacelo siempre **antes** del push, en la intimidad de tu local en una branch que solo estas laburando vos.

---

### 10~ Comandos utiles 🪛


| Si queres... | Usas... |
| :--- | :--- |
| **Ver el mapa de ramas de colores** | `git log --oneline --graph --all` |
| **Ver qué esta guardado en el stage** | `git status` |
| **Comparar el laburo con el del origin** | `git diff HEAD..origin/main` |
| **Muestra el historial de las acciones de un repo* | `git reflog` |


---

### 11~ Reset vs Revert ⏪

### El comando `git reset` tiene dos flags claves que tenes que saber.

  -  El reset "soft" mueve tu HEAD a el commit que le indiques. Este mantiene los archivos modificados desde que se hizo el commit, es decir, los cambios posteriores

  -  El reset "hard" este como el anterior, mueve tu HEAD hacia el commit que le indiques.
     La diferencia es que este borra todos los commits posteriores que se han hecho desde el commit que le indicaste

> Podes usarlos utilizando `git reset --soft HEAD~2` o `git reset --hard HEAD~2` dependiendo de tu caso concreto.<br>
> _(en este ejemplo estamos volviendo hacia atras 2 commits detras del HEAD "~2")_

### El comando `git revert` es mas sencillo

  -  Este agrega un commit a el historial de commits que revierte el ultimo commit que se haya hecho

> Podes usarlo utilizando `git revert (commit)`.

---

### 12~ Cherry pick 🍒
  -  Crea un nuevo commit con los cambios que el commit indicado introdujo. Para evitar commits vacios, el cherry pick aplica por defecto los cambios que la rama no tiene

> Podes usarlo utilizando `git cherry-pick (commit)`.

---

### 13~ Visual reference: Merge, Cherry Pick & Rebase

<img width="1383" height="788" alt="image" src="https://github.com/user-attachments/assets/760b423e-fe5a-40ef-99c1-e31c2d1f67c9" />
<br>

> Source: [The Modern Coder Video on Cherry Picking](https://www.youtube.com/watch?v=i657Bg_HAWI)

---

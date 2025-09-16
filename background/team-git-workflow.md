# Team Git Workflow

## Intro
Teams need a consistent workflow to avoid conflicts and keep code organized.

## Goals
- Use feature branches for development
- Create pull requests and request reviews
- Resolve merge conflicts correctly
- Use tags and releases for competition versions

---

## 1. **Repository Setup**

* Create a central GitHub repository for the robot code (e.g., `FRC-2025-Robot`).
* Initial files:

  * `src/main/java` → main robot code
  * `src/test/java` → test code (optional but encouraged)
  * `README.md` → overview of repo
  * `.gitignore` → ignore build files, logs, Gradle cache

---

## 2. **Branching Strategy**

* **`main`**

  * Always contains *stable, competition-ready* code.
  * Protected branch → requires pull request (PR) and review.
* **`dev`**

  * Integration branch where tested features are merged.
* **Feature branches**

  * Each feature, fix, or experiment gets its own branch:

    ```
    feature/intake
    fix/shooter-motor
    test/vision-prototype
    ```

---

## 3. **Normal Workflow**

1. **Start work**

   ```bash
   git checkout dev
   git pull origin dev
   git checkout -b feature/drive-tuning
   ```
2. **Write code & commit often**

   ```bash
   git add .
   git commit -m "Implement PID tuning for drive motors"
   ```
3. **Push to GitHub**

   ```bash
   git push origin feature/drive-tuning
   ```
4. **Open a Pull Request** → Merge into `dev` after review.
5. **Test on robot** → Once verified, merge `dev` → `main`.

---

## 4. **Formal Release Process**

When code on `main` is stable (after testing on a robot), follow this release process:

### Step 1: Tag the Release

```bash
git checkout main
git pull origin main
git tag -a v2025.1 -m "Week 1 competition build"
git push origin v2025.1
```

### Step 2: Create a GitHub Release

1. Go to your repository on GitHub → **Releases** → **Draft a new release**.
2. Select the tag (`v2025.1`).
3. Fill in release notes:

   * **Title**: `Week 1 Competition Build`
   * **Description**:

     * Key features added (e.g., autonomous paths, shooter PID tuned)
     * Known issues or limitations
     * Setup instructions if needed
4. Publish the release.

### Step 3: Deploy the Release

* Use only code from a tagged release (`main`) for competitions.
* Driver Station laptops should clone or pull the specific release.
* Keep multiple releases for reference:

  * `v2025.0` → Initial robot code
  * `v2025.1` → Week 1 comp build
  * `v2025.2` → Post-fixes for Week 2

---

## 5. **Competition Workflow**

* Before leaving for an event:

  * Merge tested code into `main`.
  * Tag & publish a GitHub release (e.g., `v2025.1`).
  * Deploy this release to the Driver Station laptop(s).
* During competition (with limited internet):

  * Commit fixes locally.
  * Once stable, merge to `main` → tag `v2025.1.1`.
  * Push when internet is available.

---

## 6. **Best Practices**

* **Commit early, commit often** → small changes are easier to debug.
* **Protect `main`** → no direct pushes, always via PR + review.
* **Use semantic versioning for releases**:

  * `vYEAR.MAJOR.MINOR` → `v2025.1.0`, `v2025.1.1`, etc.
* **Document in releases** → future programmers (and your drive team) know what’s in each build.

---

✅ This workflow gives your team a **clear development cycle**: feature branches → `dev` → tested → `main` → **formal release**.

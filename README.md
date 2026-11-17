# StudyLock

A strict study app for Android that blocks distracting apps and websites and does not let you cancel a session once it starts.

**Current state: Stage 1.** The app installs, opens and shows four screens. It does NOT block anything yet. See `STATUS.md` for what is done and what is not.

---

## Part A: Put the files into your repository (phone only)

You need the ZIP file named `StudyLock.zip` on your phone, and your repository at github.com/morefa0382/StudyLock.

GitHub's phone website cannot upload a ZIP and unpack it. It uploads individual files and folders. So first unpack the ZIP on your phone:

1. Open the **My Files** app on your Samsung phone and find `StudyLock.zip` (usually in Downloads).
2. Tap the ZIP, then tap **Extract** (or **Extract here**). A folder called `StudyLock` appears.

Then upload to GitHub:

3. In Chrome, open **github.com/morefa0382/StudyLock** and sign in.
4. Tap the browser menu (three dots) and turn on **Desktop site**. The upload page works much better this way.
5. Tap **Add file**, then **Upload files**.
6. Tap the **choose your files** link. In the file picker, open the extracted `StudyLock` folder and select everything inside it.
   - If the picker does not let you pick folders, you may need to upload folder by folder. The important thing is that the final repository has the same folder layout as the ZIP, for example `app/src/main/...`.
7. **Check the hidden folder:** the folder `.github` is hidden on many phones, and it contains the build recipe (`.github/workflows/build.yml`). If it is missing from the upload, see Part A2 below.
8. Scroll down, leave "Commit directly to the main branch" selected, and tap **Commit changes**.

### Part A2: If `.github` did not upload

1. In your repository, tap **Add file**, then **Create new file**.
2. In the name box type exactly: `.github/workflows/build.yml` (typing the slashes makes the folders).
3. Open `build.yml` from the extracted folder on your phone (any text editor), copy everything, and paste it into the big box on GitHub.
4. Tap **Commit changes**.

---

## Part B: Build the APK in the cloud

1. In your repository, tap the **Actions** tab. If asked, tap the green button that enables workflows.
2. A run called **Build debug APK** starts by itself after your upload. If it does not, tap **Build debug APK** on the left, then **Run workflow**, then the green **Run workflow** button.
3. Wait about 5 to 10 minutes. A yellow dot means running, a green check means success, a red cross means failure.
4. **If it shows a red cross:** open the run, tap the failed step, and send me a screenshot or copy of the error text. Do not try to fix it yourself. Build failures are normal at this stage and I will fix them.
5. **If it shows a green check:** open the run, scroll to the bottom to **Artifacts**, and tap **StudyLock-debug-apk** to download it. It arrives as a ZIP containing `app-debug.apk`. Extract it with My Files.

---

## Part C: Install on your Galaxy S24 FE

1. Tap `app-debug.apk`. Android will ask you to allow installs from this source. Allow it for My Files or Chrome, whichever is asking.
2. If the install is blocked, open **Settings, Security and privacy, Auto Blocker** and turn it off temporarily. This is a Samsung feature that blocks installs from outside the Galaxy Store. You can turn it back on afterwards, although later stages may need it off again.
3. Tap **Install**, then **Open**.

You should see StudyLock with four tabs at the bottom (Home, Session, Apps, Status). The Home screen says blocking is NOT ACTIVE. That is correct for Stage 1.

---

## Folder layout

| Path | What it is |
|---|---|
| `.github/workflows/build.yml` | The cloud build recipe |
| `build.gradle.kts`, `settings.gradle.kts`, `gradle.properties` | Project-wide build settings |
| `app/build.gradle.kts` | App build settings and libraries |
| `app/debug.keystore` | Fixed key so new builds install over old ones |
| `app/src/main/AndroidManifest.xml` | App declaration |
| `app/src/main/java/com/studylock/app/` | Kotlin source code |
| `app/src/main/res/` | Icons, text and themes |
| `STATUS.md` | Honest record of what works |

## Technical notes

- Built with Kotlin 2.3.21, Jetpack Compose (BOM 2025.12.01), Material 3, Android Gradle Plugin 8.13.0, Gradle 8.13, Java 17.
- Compiled against Android API 36. It runs on Android 17 and One UI 9. A move to API 37 is planned later.
- The build uses the Gradle version installed by the workflow, so no Gradle wrapper files are needed.

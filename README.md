# Git Assignment - Hero Vired

## Repository Name: `git_assignment_HeroVired`

This repository contains multiple features and workflows demonstrating Git operations, feature branching, Git LFS integration, and Git stash management.

---

## Q.1: CalculatorPlus - Implementing Square Root Feature

### **Project Overview**
`CalculatorPlus` is a Python application that performs basic arithmetic operations such as addition, subtraction, multiplication, and division. A new feature to calculate the square root of a number is to be added.

### **Workflow Steps**

#### **1. Repository Setup**
- Create a GitHub repository: `git_assignment_HeroVired`
- Clone the repository:
  ```sh
  git clone <repository_url>
  cd git_assignment_HeroVired
  ```
- Create a `dev` branch:
  ```sh
  git checkout -b dev
  ```

#### **2. Add Initial Code to `dev` Branch**
- Commit and push changes:
  ```sh
  git add calculator.py
  git commit -m "Added initial CalculatorPlus code"
  git push origin dev
  ```

#### **3. Merging `dev` into `main` and Releasing v1**
```sh
  git checkout main
  git merge dev
  git tag v1.0
  git push origin main --tags
```

#### **4. Adding Collaborators**
Invite classmates as collaborators in GitHub under **Settings > Collaborators**.

#### **5. Implement Square Root Feature in `feature/sqrt` Branch**
```sh
  git checkout -b feature/sqrt
```
Modify the `Calculator` class:

- Commit and push:
  ```sh
  git add calculator.py
  git commit -m "Implemented square root feature"
  git push origin feature/sqrt
  ```

#### **6. Handling a Critical Bug in `dev` Branch**
While working on `feature/sqrt`, a bug is found in the `divide` function. Fix it by switching to `dev`:
```sh
  git checkout dev
```
Modify the `divide` function:
- Commit and push:
  ```sh
  git add calculator.py
  git commit -m "Fixed divide function to prevent division by zero"
  git push origin dev
  ```
- Merge the fix into `feature/sqrt`:
  ```sh
  git checkout feature/sqrt
  git merge dev
  ```

#### **7. Creating Pull Request and Merging**
- Create a Pull Request (PR) from `feature/sqrt` to `dev`.
- Request a code review and make necessary changes.
- Merge `feature/sqrt` into `dev` after approval.

#### **8. Final Testing and Release v2**
- Merge `dev` into `main` and release v2:
  ```sh
  git checkout main
  git merge dev
  git tag v2.0
  git push origin main --tags
  ```

---

## Q.2: Git LFS for Large Binary Files

### **Workflow Steps**

#### **1. Create `lfs` Branch and Configure Git LFS**
```sh
  git checkout -b lfs
  git lfs install
  git lfs track "*.bin"
```

#### **2. Add and Push a Large File (200MB+)**
```sh
  dd if=/dev/zero of=large_file.bin bs=1M count=210  # Linux/macOS
  fsutil file createnew large_file.bin 220000000     # Windows
  git add .gitattributes large_file.bin
  git commit -m "Added large binary file"
  git push origin lfs
```

#### **3. Clone on Another Machine and Verify**
```sh
  git clone <repository_url>
  cd git_assignment_HeroVired
  git checkout lfs
  git lfs pull
```

---

## Q.3: Geometry Calculator with Git Stash

### **Workflow Steps**

#### **1. Create `geometry-calculator` Branch**
```sh
  git checkout -b geometry-calculator
```

#### **2. Implement Features in Separate Branches with Stashing**

##### **Circle Area Feature**
```sh
  git checkout -b feature/circle-area
```
Modify `geometry_calculator.py` for circle area, then stash:
```sh
  git stash
  git checkout -b feature/rectangle-area
```

##### **Rectangle Area Feature**
Modify `geometry_calculator.py` for rectangle area, then stash:
```sh
  git stash
```

##### **Switch Back to Circle Area Branch and Finalize It**
```sh
  git checkout feature/circle-area
  git stash pop
  git commit -m "Implemented circle area feature"
  git push origin feature/circle-area
```

##### **Switch Back to Rectangle Area Branch and Finalize It**
```sh
  git checkout feature/rectangle-area
  git stash pop
  git commit -m "Implemented rectangle area feature"
  git push origin feature/rectangle-area
```

#### **3. Create and Merge Pull Requests**
- Create PRs from `feature/circle-area` and `feature/rectangle-area` to `dev`.
- Merge both after review.
- Merge `dev` into `main`.

---

## 🎯 **Conclusion**
This repository demonstrates Git best practices, including:
- Feature branching, merging, and stashing
- Git LFS for handling large files
- Fixing critical bugs while maintaining separate features
- Creating pull requests and managing releases

Happy coding! 🚀


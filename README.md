# iOS-SwiftLint

Please place this repository like the following structure.

In the same level as your project level and follow the instruction. 

```
iOS-SwiftLint
│   README.md
│   .swiftlint.yml  
------------------------------
ProjectName
│   README.md
│   ProjectName.xcodeproj  
│
└───folder1
│   │   file011.swift
│   │   file012.swift
│   │
│   └───subfolder1
│       │   file111.swift
│       │   file112.swift
│       │   ...
│   
└───folder2
    │   file021.swift
    │   file022.swift
```


1. Select the project document in the Project navigator.
1. Select the **Build Phases** tab.
1. Click **+** and choose **New Run Script Phase**.
4. Drag the new phase before the **Compile Sources** phase.
4. Click the disclosure triangle on the **Run Script** phase and ensure **Shell** is set to **/bin/sh**.
6. Add the following script:

```
export PATH="$PATH:/opt/homebrew/bin"

if [ -f ../iOS-SwiftLint/.swiftlint.yml ]; then
  if which swiftlint >/dev/null; then
    swiftlint --no-cache --config ../iOS-SwiftLint/.swiftlint.yml
  else
    echo "warning: SwiftLint not installed, download from https://github.com/realm/SwiftLint"
  fi
else
  echo "error: SwiftLint configuration not fetched, download from https://github.com/skat/iOS-SwiftLint and put the folder as the same level as your project folder"
fi
```

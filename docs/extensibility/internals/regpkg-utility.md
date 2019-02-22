---
title: RegPkg Utility | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b9b07bc801e687da9ce93968dbac59966328484
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619241"
---
# <a name="regpkg-utility"></a>Narzędzie RegPkg
> [!NOTE]
>  Jest preferowanym sposobem rejestrowanie pakietów w programie Visual Studio przy użyciu plików .pkgdef. Pozwala to na rozszerzenie wdrożenia bez potrzeby dostępu do rejestru systemu, która jest wymagana dla wdrożenia VSIX. Pkgdef pliki są tworzone za pomocą [narzędzie CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Aby uzyskać więcej informacji na temat wdrażania pakietu Visual Studio, zobacz [wysyłania rozszerzenia programu Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 Narzędzie RegPkg.exe rejestruje pakietów VSPackage przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i przygotowuje je do wdrożenia. To narzędzie jest używany w tle podczas programowania pakietu VSPackage. Działa jako część procesu kompilacji, aby możesz skompilować i uruchomić pakietu VSPackage w gałęzi eksperymentalne.

 RegPkg można wygenerować skryptów rejestru systemu w różnych formatach. Można zastosować tych skryptów w projektach wdrożenia, takich jak projekty msi lub pliki zestaw narzędzi XML Instalatora Windows.

 RegPkg.exe znajduje się zwykle w \< *ścieżka instalacji programu Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg poniżej następującej składni:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /Root:root wykonanie rejestracji o określonej nazwie.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] element główny.

 /RegFile:filename tworzy plik .reg, a nie aktualizacji rejestru.  Nie można używać z /vrgfile lub /rgsfile lub /wixfile.

 /rgsfile:filename tworzy plik .rgs, a nie aktualizacji rejestru.  Nie można używać z /vrgfile lub/regfile razem lub /wixfile.

 /vrgfile:filename tworzy plik .vrg, a nie aktualizacji rejestru.  Nie można używać z/regfile razem lub /rgsfile lub /wixfile.

 /rgm tworzy plik .rgm oprócz pliku rgs.  Musi być łączona z /rgsfile.

 /wixfile:filename tworzy plik zgodnego zestawu narzędzi XML Instalatora Windows, a nie aktualizacji rejestru.  Nie można używać z/regfile razem lub /rgsfile lub /vrgfile.

 / codebase wymusza rejestracji w bazie kodu, a nie zestaw.

 / Assembly wymusza rejestrację przy użyciu zestawu, a nie bazy kodu.

 / unregister Unregisters tego pakietu.  Nie można użyć

 / regfile razem lub /vrgfile lub /rgsfile albo /wixfile.

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
- [Rozwiązywanie problemów z rejestracją pakietu RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
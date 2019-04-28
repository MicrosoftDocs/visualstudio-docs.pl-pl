---
title: Rozwiązywanie problemów z rejestracją pakietu RegPkg | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12beb4bda419c99c013a324b08b92bf3ff5365dd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429869"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Rozwiązywanie problemów z rejestracją pakietu RegPkg
> [!NOTE]
> Jest preferowanym sposobem rejestrowanie pakietów w programie Visual Studio przy użyciu plików .pkgdef. Pozwala to na rozszerzenie wdrożenia bez potrzeby uzyskania dostępu do rejestru systemu. Pkgdef pliki są tworzone za pomocą [narzędzie CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Aby zarejestrować pakiet za pomocą RegPkg w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], należy użyć wersji RegPkg, który jest odpowiedni dla Twojego pakietu.

## <a name="regpkg-versions-related-to-package-versions"></a>Wersje RegPkg związane z wersji pakietu
 Istnieją dwie wersje RegPkg. Wersja jednego jest zawarta w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ta wersja umożliwia rejestrowanie pakietów, które zostały skompilowane przy użyciu jednej z następujących zestawów:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Go nie można zarejestrować pakiety, które zostały skompilowane przy użyciu starszych zestawu Microsoft.VisualStudio.Shell.dll.

   Starszą wersję RegPkg można zarejestrować pakiety, które zostały skompilowane przy użyciu zestawu Microsoft.VisualStudio.Shell.dll. Jednak nie można go zarejestrować pakiety skompilowane przy użyciu nowszej wersji tego zestawu.

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
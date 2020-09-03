---
title: Rozwiązywanie problemów z rejestracją pakietu RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5266579ff235a0f6c4f3e555d79d5a00de2c194
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87234864"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Rozwiązywanie problemów z rejestracją pakietu RegPkg
> [!NOTE]
> Preferowanym sposobem rejestrowania pakietów w programie Visual Studio jest użycie plików. pkgdef. Pozwala to na wdrażanie rozszerzeń bez konieczności uzyskiwania dostępu do rejestru systemowego. Pliki pkgdef są tworzone za pomocą [Narzędzia CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Aby zarejestrować pakiet za pomocą RegPkg w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , należy użyć wersji RegPkg, która jest odpowiednia dla Twojego pakietu.

## <a name="regpkg-versions-related-to-package-versions"></a>Wersje RegPkg związane z wersjami pakietów
 Istnieją dwie wersje programu RegPkg. Jedna wersja jest dołączona do programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Ta wersja służy do rejestrowania pakietów, które zostały skompilowane przy użyciu jednego z następujących zestawów:

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   Nie można zarejestrować pakietów, które zostały skompilowane przy użyciu wcześniejszego zestawu Microsoft.VisualStudio.Shell.dll.

   Wcześniejsza wersja RegPkg może rejestrować pakiety, które zostały skompilowane przy użyciu zestawu Microsoft.VisualStudio.Shell.dll. Nie może jednak rejestrować pakietów utworzonych przy użyciu nowszych wersji tego zestawu.

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
- [Rozwiązywanie problemów z programem Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)

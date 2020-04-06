---
title: Rozwiązywanie problemów z rejestracją pakietu RegPkg | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebae9f7c5b4d1a6dcfee20c3b36c02f8ead2e0bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704326"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Rozwiązywanie problemów z rejestracją pakietu RegPkg
> [!NOTE]
> Preferowanym sposobem rejestrowania pakietów w programie Visual Studio jest użycie plików pkgdef. Pozwala to na wdrożenie rozszerzenia bez konieczności uzyskiwania dostępu do rejestru systemu. Pliki Pkgdef są tworzone przy użyciu [narzędzia CreatePkgDef.](../../extensibility/internals/createpkgdef-utility.md)

 Aby zarejestrować pakiet przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]programu RegPkg w programie , należy użyć wersji programu RegPkg, która jest odpowiednia dla danego pakietu.

## <a name="regpkg-versions-related-to-package-versions"></a>Wersje RegPkg związane z wersjami pakietowymi
 Istnieją dwie wersje regpkg. Jedna wersja jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zawarta w . Ta wersja służy do rejestrowania pakietów, które zostały utworzone przy użyciu jednego z następujących zestawów:

1. Plik DLL programu Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Plik DLL programu Microsoft.VisualStudioShell.11.0.dll

   Nie można zarejestrować pakietów, które zostały utworzone przy użyciu wcześniejszego zestawu Microsoft.VisualStudio.Shell.dll.

   Wcześniejsza wersja programu RegPkg może rejestrować pakiety utworzone przy użyciu zestawu Microsoft.VisualStudio.Shell.dll. Jednak nie można zarejestrować pakiety utworzone przy użyciu nowszych wersji tego zestawu.

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)

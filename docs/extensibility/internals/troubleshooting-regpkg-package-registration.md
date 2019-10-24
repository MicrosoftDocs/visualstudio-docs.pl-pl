---
title: Rozwiązywanie problemów z rejestracją pakietu RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 386a1a17c036207d122e4b3c7cb142a628dcfe38
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722276"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Rozwiązywanie problemów z rejestracją pakietu RegPkg
> [!NOTE]
> Preferowanym sposobem rejestrowania pakietów w programie Visual Studio jest użycie plików. pkgdef. Pozwala to na wdrażanie rozszerzeń bez konieczności uzyskiwania dostępu do rejestru systemowego. Pliki pkgdef są tworzone za pomocą [Narzędzia CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).

 Aby zarejestrować pakiet za pomocą RegPkg w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], musisz użyć wersji RegPkg, która jest odpowiednia dla Twojego pakietu.

## <a name="regpkg-versions-related-to-package-versions"></a>Wersje RegPkg związane z wersjami pakietów
 Istnieją dwie wersje programu RegPkg. Jedna wersja jest dołączona do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ta wersja służy do rejestrowania pakietów, które zostały skompilowane przy użyciu jednego z następujących zestawów:

1. Microsoft. VisualStudioShell. 9.0. dll

2. Microsoft. VisualStudioShell. 10.0. dll

3. Microsoft. VisualStudioShell. 11.0. dll

   Nie można zarejestrować pakietów, które zostały skompilowane przy użyciu wcześniejszego zestawu Microsoft. VisualStudio. Shell. dll.

   Wcześniejsza wersja RegPkg może rejestrować pakiety, które zostały skompilowane przy użyciu zestawu Microsoft. VisualStudio. Shell. dll. Nie może jednak rejestrować pakietów utworzonych przy użyciu nowszych wersji tego zestawu.

## <a name="see-also"></a>Zobacz także
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
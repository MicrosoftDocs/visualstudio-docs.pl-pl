---
title: Rozwiązywanie problemów z rejestracją pakietu RegPkg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 241975e475252a18d5e5a91c6e8c4fb40c067a95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807444"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Rozwiązywanie problemów z rejestracją pakietu RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Preferowanym sposobem rejestrowania pakietów w programie Visual Studio jest użycie plików. pkgdef. Pozwala to na wdrażanie rozszerzeń bez konieczności uzyskiwania dostępu do rejestru systemowego. Pliki pkgdef są tworzone za pomocą [Narzędzia CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Aby zarejestrować pakiet za pomocą RegPkg w programie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , należy użyć wersji RegPkg, która jest odpowiednia dla Twojego pakietu.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Wersje RegPkg związane z wersjami pakietów  
 Istnieją dwie wersje programu RegPkg. Jedna wersja jest dołączona do programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Ta wersja służy do rejestrowania pakietów, które zostały skompilowane przy użyciu jednego z następujących zestawów:  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   Nie można zarejestrować pakietów, które zostały skompilowane przy użyciu wcześniejszego zestawu Microsoft.VisualStudio.Shell.dll.  
  
   Wcześniejsza wersja RegPkg może rejestrować pakiety, które zostały skompilowane przy użyciu zestawu Microsoft.VisualStudio.Shell.dll. Nie może jednak rejestrować pakietów utworzonych przy użyciu nowszych wersji tego zestawu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zwalnianie produktu](../../misc/releasing-a-visual-studio-integration-product.md)

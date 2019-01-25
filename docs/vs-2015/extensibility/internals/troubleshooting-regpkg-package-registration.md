---
title: Rozwiązywanie problemów z rejestracją pakietu RegPkg | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6337562ff7a043c225dac678cb846cc76384c03c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771239"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Rozwiązywanie problemów z rejestracją pakietu RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
>  Jest preferowanym sposobem rejestrowanie pakietów w programie Visual Studio przy użyciu plików .pkgdef. Pozwala to na rozszerzenie wdrożenia bez potrzeby uzyskania dostępu do rejestru systemu. Pkgdef pliki są tworzone za pomocą [narzędzie CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md).  
  
 Aby zarejestrować pakiet za pomocą RegPkg w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], należy użyć wersji RegPkg, który jest odpowiedni dla Twojego pakietu.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>Wersje RegPkg związane z wersji pakietu  
 Istnieją dwie wersje RegPkg. Wersja jednego jest zawarta w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Ta wersja umożliwia rejestrowanie pakietów, które zostały skompilowane przy użyciu jednej z następujących zestawów:  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   Go nie można zarejestrować pakiety, które zostały skompilowane przy użyciu starszych zestawu Microsoft.VisualStudio.Shell.dll.  
  
   Starszą wersję RegPkg można zarejestrować pakiety, które zostały skompilowane przy użyciu zestawu Microsoft.VisualStudio.Shell.dll. Jednak nie można go zarejestrować pakiety skompilowane przy użyciu nowszej wersji tego zestawu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zwalnianie produktu](../../misc/releasing-a-visual-studio-integration-product.md)

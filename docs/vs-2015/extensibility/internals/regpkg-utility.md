---
title: Narzędzie RegPkg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1895d3b57e5109f824728021cb1d64f0c527384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64819771"
---
# <a name="regpkg-utility"></a>Narzędzie RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Preferowanym sposobem rejestrowania pakietów w programie Visual Studio jest użycie plików. pkgdef. Pozwala to na wdrożenie rozszerzenia bez konieczności uzyskiwania dostępu do rejestru systemowego, który jest wymaganiem wdrożenia VSIX. Pliki pkgdef są tworzone za pomocą [Narzędzia CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Aby uzyskać więcej informacji na temat wdrażania pakietu programu Visual Studio, zobacz [wysyłanie rozszerzeń programu Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Narzędzie RegPkg.exe rejestruje pakietu VSPackage z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i przygotowuje go do wdrożenia. To narzędzie jest używane w tle podczas opracowywania pakietu VSPackage. Działa w ramach procesu kompilacji, dzięki czemu można kompilować i uruchamiać pakietu VSPackage w eksperymentalnym elemencie Hive.  
  
 RegPkg może generować skrypty rejestru systemowego w kilku formatach. Te skrypty można dołączyć do projektów wdrażania, takich jak projekty MSI lub Instalator Windows pliki zestawu narzędzi XML.  
  
 RegPkg.exe zwykle znajduje się w \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg ma następującą składnię:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root: główny  
 Wykonuje rejestrację pod określonym  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pierwiastek.  
  
 /regfile: FileName  
 Tworzy plik reg zamiast aktualizować rejestr.  Nie można używać z/vrgfile lub/rgsfile lub/wixfile.  
  
 /rgsfile: FileName  
 Tworzy plik. RGS, a nie aktualizuje rejestru.  Nie można używać z/vrgfile lub/regfile lub/wixfile.  
  
 /vrgfile: FileName  
 Tworzy plik. VRG, a nie aktualizuje rejestru.  Nie można używać z/regfile lub/rgsfile lub/wixfile.  
  
 /rgm  
 Tworzy plik. RGM oprócz pliku RGS.  Muszą być połączone z/rgsfile.  
  
 /wixfile: FileName  
 Tworzy plik zgodny z zestawem narzędzi XML Instalator Windows, zamiast aktualizować rejestr.  Nie można używać z/regfile lub/rgsfile lub/vrgfile.  
  
 /codebase  
 Wymusza rejestrację z użyciem bazy kodu, a nie zestawu.  
  
 /Assembly  
 Wymusza rejestrację z zestawem, a nie z bazą kodu.  
  
 /Unregister  
 Wyrejestrowuje ten pakiet.  Nie można użyć  
  
 z/regfile lub/vrgfile lub/rgsfile lub/wixfile.  
  
## <a name="see-also"></a>Zobacz też  
 [Zwalnianie produktu](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Rozwiązywanie problemów z rejestracją pakietu RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)

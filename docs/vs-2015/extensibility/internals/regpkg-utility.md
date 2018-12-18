---
title: Narzędzie RegPkg | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da637b365eec260a7c1c34bbe7ba96c785cc18fc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781286"
---
# <a name="regpkg-utility"></a>Narzędzie RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
>  Jest preferowanym sposobem rejestrowanie pakietów w programie Visual Studio przy użyciu plików .pkgdef. Pozwala to na rozszerzenie wdrożenia bez potrzeby dostępu do rejestru systemu, która jest wymagana dla wdrożenia VSIX. Pkgdef pliki są tworzone za pomocą [narzędzie CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Aby uzyskać więcej informacji na temat wdrażania pakietu Visual Studio, zobacz [wysyłania rozszerzenia programu Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Narzędzie RegPkg.exe rejestruje pakietów VSPackage przy użyciu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i przygotowuje je do wdrożenia. To narzędzie jest używany w tle podczas programowania pakietu VSPackage. Działa jako część procesu kompilacji, aby możesz skompilować i uruchomić pakietu VSPackage w gałęzi eksperymentalne.  
  
 RegPkg można wygenerować skryptów rejestru systemu w różnych formatach. Można zastosować tych skryptów w projektach wdrożenia, takich jak projekty msi lub pliki zestaw narzędzi XML Instalatora Windows.  
  
 RegPkg.exe znajduje się zwykle w \< *ścieżka instalacji programu Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg poniżej następującej składni:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /Root:root  
 Przeprowadza rejestrację o określonej nazwie.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] element główny.  
  
 /RegFile:filename  
 Tworzy plik .reg, a nie aktualizacji rejestru.  Nie można używać z /vrgfile lub /rgsfile lub /wixfile.  
  
 /rgsfile:filename  
 Tworzy plik .rgs, a nie aktualizacji rejestru.  Nie można używać z /vrgfile lub/regfile razem lub /wixfile.  
  
 /vrgfile:filename  
 Tworzy plik .vrg, a nie aktualizacji rejestru.  Nie można używać z/regfile razem lub /rgsfile lub /wixfile.  
  
 /rgm  
 Tworzy plik .rgm oprócz pliku rgs.  Musi być łączona z /rgsfile.  
  
 /wixfile:filename  
 Tworzy plik zgodnego zestawu narzędzi XML Instalatora Windows, a nie aktualizacji rejestru.  Nie można używać z/regfile razem lub /rgsfile lub /vrgfile.  
  
 /codebase  
 Wymusza rejestrację przy użyciu kodu, a nie zestaw.  
  
 / Assembly  
 Wymusza rejestrację przy użyciu zestawu, a nie bazy kodu.  
  
 / unregister  
 Wyrejestrowuje tego pakietu.  Nie można użyć  
  
 / regfile razem lub /vrgfile lub /rgsfile albo /wixfile.  
  
## <a name="see-also"></a>Zobacz też  
 [Zwalnianie produktu](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Rozwiązywanie problemów z rejestracją pakietu RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)


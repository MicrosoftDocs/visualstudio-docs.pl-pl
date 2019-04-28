---
title: RegPkg Utility | Microsoft Docs
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436586"
---
# <a name="regpkg-utility"></a>Narzędzie RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Jest preferowanym sposobem rejestrowanie pakietów w programie Visual Studio przy użyciu plików .pkgdef. Pozwala to na rozszerzenie wdrożenia bez potrzeby dostępu do rejestru systemu, która jest wymagana dla wdrożenia VSIX. Pkgdef pliki są tworzone za pomocą [narzędzie CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Aby uzyskać więcej informacji na temat wdrażania pakietu Visual Studio, zobacz [wysyłania rozszerzenia programu Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Narzędzie RegPkg.exe rejestruje pakietów VSPackage przy użyciu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i przygotowuje je do wdrożenia. To narzędzie jest używany w tle podczas programowania pakietu VSPackage. Działa jako część procesu kompilacji, aby możesz skompilować i uruchomić pakietu VSPackage w gałęzi eksperymentalne.  
  
 RegPkg można wygenerować skryptów rejestru systemu w różnych formatach. Można zastosować tych skryptów w projektach wdrożenia, takich jak projekty msi lub pliki zestaw narzędzi XML Instalatora Windows.  
  
 RegPkg.exe znajduje się zwykle w \< *ścieżka instalacji programu Visual Studio SDK*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg poniżej następującej składni:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 Przeprowadza rejestrację o określonej nazwie.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] element główny.  
  
 /regfile:FileName  
 Tworzy plik .reg, a nie aktualizacji rejestru.  Nie można używać z /vrgfile lub /rgsfile lub /wixfile.  
  
 /rgsfile:FileName  
 Tworzy plik .rgs, a nie aktualizacji rejestru.  Nie można używać z /vrgfile lub/regfile razem lub /wixfile.  
  
 /vrgfile:FileName  
 Tworzy plik .vrg, a nie aktualizacji rejestru.  Nie można używać z/regfile razem lub /rgsfile lub /wixfile.  
  
 /rgm  
 Tworzy plik .rgm oprócz pliku rgs.  Musi być łączona z /rgsfile.  
  
 /wixfile:FileName  
 Tworzy plik zgodnego zestawu narzędzi XML Instalatora Windows, a nie aktualizacji rejestru.  Nie można używać z/regfile razem lub /rgsfile lub /vrgfile.  
  
 /codebase  
 Wymusza rejestrację przy użyciu kodu, a nie zestaw.  
  
 / Assembly  
 Wymusza rejestrację przy użyciu zestawu, a nie bazy kodu.  
  
 /unregister  
 Wyrejestrowuje tego pakietu.  Nie można użyć  
  
 / regfile razem lub /vrgfile lub /rgsfile albo /wixfile.  
  
## <a name="see-also"></a>Zobacz też  
 [Zwalnianie produktu](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Rozwiązywanie problemów z rejestracją pakietu RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)

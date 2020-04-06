---
title: Narzędzie RegPkg | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cebfd7a9782a2760eb33f7e56bfe16b126fc6251
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705635"
---
# <a name="regpkg-utility"></a>Narzędzie RegPkg
> [!NOTE]
> Preferowanym sposobem rejestrowania pakietów w programie Visual Studio jest użycie plików pkgdef. Pozwala to na wdrożenie rozszerzenia bez konieczności uzyskiwania dostępu do rejestru systemu, co jest wymagane dla wdrożenia VSIX. Pliki Pkgdef są tworzone przy użyciu [narzędzia CreatePkgDef.](../../extensibility/internals/createpkgdef-utility.md) Aby uzyskać więcej informacji na temat wdrażania pakietu programu Visual Studio, zobacz [Wysyłka rozszerzeń programu Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 Narzędzie RegPkg.exe rejestruje vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] z i przygotowuje go do wdrożenia. To narzędzie jest używane w tle podczas tworzenia vspackage. Działa jako część procesu kompilacji, dzięki czemu można skompilować i uruchomić VSPackage w gałęzi eksperymentalnej.

 RegPkg może generować skrypty rejestru systemowego w kilku formatach. Te skrypty można włączyć do projektów wdrażania, takich jak projekty msi lub pliki XML Zestawu Narzędzi Instalatora Windows.

 Program RegPkg.exe zazwyczaj \<znajduje się w *ścieżce instalacji zestawu SDK programu Visual Studio*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg jest następująca:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Wykonuje rejestrację w określonym

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Głównego.

 /regfile:Nazwa pliku Tworzy plik reg zamiast aktuwania rejestru.  Nie można używać z /vrgfile lub /rgsfile lub /wixfile.

 /rgsfile:FileName Tworzy plik .rgs zamiast aktualizować rejestr.  Nie można używać z /vrgfile lub /regfile lub /wixfile.

 /vrgfile:FileName Tworzy plik .vrg zamiast aktualizować rejestr.  Nie można używać z /regfile lub /rgsfile lub /wixfile.

 /rgm Tworzy plik .rgm oprócz pliku rgs.  Musi być połączony z /rgsfile.

 /wixfile:FileName Tworzy plik zgodny z narzędziami XML Instalatora Windows, a nie aktualizuje rejestr.  Nie można używać z /regfile lub /rgsfile lub /vrgfile.

 /codebase Wymusza rejestrację z CodeBase, a nie Assembly.

 /assembly Wymusza rejestrację z zestawem, a nie codebase.

 /wyrejestrować Wyrejestruje ten pakiet.  Nie można używać

 z /regfile lub /vrgfile lub /rgsfile lub /wixfile.

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
- [Rozwiązywanie problemów z rejestracją pakietu RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)

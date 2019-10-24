---
title: Narzędzie RegPkg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f811eb37da730d63e199a0e378b8a9122143649e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724446"
---
# <a name="regpkg-utility"></a>Narzędzie RegPkg
> [!NOTE]
> Preferowanym sposobem rejestrowania pakietów w programie Visual Studio jest użycie plików. pkgdef. Pozwala to na wdrożenie rozszerzenia bez konieczności uzyskiwania dostępu do rejestru systemowego, który jest wymaganiem wdrożenia VSIX. Pliki pkgdef są tworzone za pomocą [Narzędzia CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Aby uzyskać więcej informacji na temat wdrażania pakietu programu Visual Studio, zobacz [wysyłanie rozszerzeń programu Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).

 Narzędzie RegPkg. exe rejestruje pakietu VSPackage z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i przygotowuje go do wdrożenia. To narzędzie jest używane w tle podczas opracowywania pakietu VSPackage. Działa w ramach procesu kompilacji, dzięki czemu można kompilować i uruchamiać pakietu VSPackage w eksperymentalnym elemencie Hive.

 RegPkg może generować skrypty rejestru systemowego w kilku formatach. Te skrypty można dołączyć do projektów wdrażania, takich jak projekty MSI lub Instalator Windows pliki zestawu narzędzi XML.

 RegPkg. exe znajduje się zazwyczaj w lokalizacji \<*ścieżka instalacji zestawu SDK programu Visual Studio*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg ma następującą składnię:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root: element główny wykonuje rejestrację pod określonym

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] główny.

 /regfile: nazwa pliku tworzy plik reg zamiast aktualizować rejestr.  Nie można używać z/vrgfile lub/rgsfile lub/wixfile.

 /rgsfile: nazwa pliku tworzy plik. RGS, a nie aktualizuje rejestru.  Nie można używać z/vrgfile lub/regfile lub/wixfile.

 /vrgfile: nazwa pliku tworzy plik. VRG, a nie aktualizuje rejestru.  Nie można używać z/regfile lub/rgsfile lub/wixfile.

 /RGM tworzy plik. RGM oprócz pliku RGS.  Muszą być połączone z/rgsfile.

 /wixfile: FileName tworzy plik zgodny Instalator Windows z zestawem narzędzi XML, a nie aktualizuje rejestru.  Nie można używać z/regfile lub/rgsfile lub/vrgfile.

 /CodeBase wymusza rejestrację z użyciem kodu bazowej, a nie zestawu.

 /Assembly wymusza rejestrację z zestawem, a nie z bazą kodu.

 /Unregister wyrejestrowuje ten pakiet.  Nie można użyć

 z/regfile lub/vrgfile lub/rgsfile lub/wixfile.

## <a name="see-also"></a>Zobacz także
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
- [Rozwiązywanie problemów z rejestracją pakietu RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
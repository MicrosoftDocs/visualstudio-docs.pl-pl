---
title: Narzędzie RegPkg | Microsoft Docs
description: Dowiedz się, jak RegPkg.exe rejestruje pakiet VSPackage w Visual Studio i przygotowuje go do wdrożenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b605d251b2e516a468401805fc0e125801129c16
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903362"
---
# <a name="regpkg-utility"></a>Narzędzie RegPkg
> [!NOTE]
> Preferowanym sposobem rejestrowania pakietów w Visual Studio jest użycie plików pkgdef. Umożliwia to wdrażanie rozszerzeń bez konieczności uzyskiwania dostępu do rejestru systemowego, co jest wymagane w przypadku wdrożenia VSIX. Pliki Pkgdef są tworzone przy użyciu [narzędzia CreatePkgDef.](../../extensibility/internals/createpkgdef-utility.md) Aby uzyskać więcej informacji na Visual Studio wdrażania pakietów, zobacz [Shipping Visual Studio Extensions](../../extensibility/shipping-visual-studio-extensions.md)(Wysyłanie Visual Studio pakietów).

 Narzędzie RegPkg.exe rejestruje pakiet VSPackage za pomocą narzędzia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i przygotowuje go do wdrożenia. To narzędzie jest używane w tle podczas opracowywania pakietów VSPackage. Jest on uruchamiany w ramach procesu kompilacji, dzięki czemu można skompilować i uruchomić pakiet VSPackage w eksperymentalnym programie Hive.

 RegPkg może generować skrypty rejestru systemu w kilku formatach. Te skrypty można uwzględnić w projektach wdrażania, takich jak .msi lub Instalator Windows XML Toolset.

 RegPkg.exe zwykle znajduje się w \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg jest zgodna z następującą składnią:

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root Wykonuje rejestrację w określonym katalogu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] głównym.

 /regfile:FileName Tworzy plik reg zamiast aktualizowania rejestru.  Nie można używać z /vrgfile lub /rgsfile lub /wixfile.

 /rgsfile:FileName Tworzy plik rgs zamiast aktualizowania rejestru.  Nie można używać z /vrgfile lub /regfile lub /wixfile.

 /vrgfile:FileName Tworzy plik vrg zamiast aktualizowania rejestru.  Nie można używać z /regfile lub /rgsfile lub /wixfile.

 /rgm Tworzy plik rgm oprócz pliku rgs.  Musi być połączony z /rgsfile.

 /wixfile:FileName Tworzy Instalator Windows zgodny z zestawem narzędzi XML, zamiast aktualizowania rejestru.  Nie można używać z /regfile lub /rgsfile lub /vrgfile.

 /codebase Wymusza rejestrację za pomocą codeBase, a nie zestawu.

 /assembly Wymusza rejestrację za pomocą zestawu, a nie CodeBase.

 /unregister Wyrejestruje ten pakiet.  Nie można użyć

 z /regfile lub /vrgfile lub /rgsfile lub /wixfile.

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)
- [Rozwiązywanie problemów z rejestracją pakietu RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)

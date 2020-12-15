---
title: Tabela poleceń programu Visual Studio (. Vsct) | Microsoft Docs
description: Więcej informacji na temat plików konfiguracji tabeli poleceń, które są plikami tekstowymi opisującymi zestaw poleceń, które zawiera pakietu VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 377bae52f506c1cb9ac0f6b2d4136faaab0b50ad
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488040"
---
# <a name="visual-studio-command-table-vsct-files"></a>Tabela poleceń programu Visual Studio (pliki Vsct)
Plik konfiguracji tabeli poleceń to plik tekstowy, który opisuje zestaw poleceń, które zawiera pakietu VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Kompilator Command Table (vsct) kompiluje pliki konfiguracyjne oparte na języku XML (pliki. vsct) do plików wyjściowych tabeli poleceń binarnych (. Dyrektor ds). Wynikowe pliki dyrektor ds są takie same jak te, które są tworzone za pomocą kompilatora Command Table (CTC), do kompilowania plików konfiguracji CTC. Jednak pliki vsct oparte na języku XML mają pewne zalety, takie jak Edytor XML i IntelliSense XML.

 Aby dowiedzieć się więcej na temat składni i semantyki plików. vsct, zobacz [Designing XML Command Table (. Vsct) — pliki](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>W tej sekcji
 [Projektowanie tabeli poleceń XML (pliki Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Opisuje sposób projektowania plików. vsct.

 [Instrukcje: tworzenie pliku Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Porównuje metody tworzenia pliku. vsct. Opisuje proces ręcznego tworzenia nowego pliku. vsct.

## <a name="related-sections"></a>Sekcje pokrewne
 [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Zawiera szczegółowe informacje o każdej sekcji pliku konfiguracyjnego XML tabeli poleceń.

 [Konfiguracja tabeli poleceń (. CTC)](/previous-versions/bb165153(v=vs.100)) przedstawia Omówienie przestarzałego formatu pliku CTC.

 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Opisuje specyfikację formatu tabeli poleceń.

 [Zasoby w pakietach VSPackage](../../extensibility/internals/resources-in-vspackages.md)

 Opisuje sposób używania zasobów zarządzanych i niezarządzanych w zarządzanych pakietów VSPackage.

 [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)

 Wyjaśnia, jak utworzyć interfejs użytkownika, który obejmuje menu, paski narzędzi i pola kombi poleceń.
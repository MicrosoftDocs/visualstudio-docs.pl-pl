---
title: Tabela poleceń programu Visual Studio (. Vsct) Pliki | Dokumenty firmy Microsoft
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
ms.openlocfilehash: d18367436d1ee1b889558a35723e4e3cec865945
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704022"
---
# <a name="visual-studio-command-table-vsct-files"></a>Tabela poleceń programu Visual Studio (pliki Vsct)
Plik konfiguracji tabeli poleceń to plik tekstowy opisujący zestaw poleceń, które zawiera pakiet VSPackage. Kompilator [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tabeli poleceń (VSCT) kompiluje pliki konfiguracyjne oparte na języku XML (pliki vsct) w binarne pliki wyjściowe tabeli poleceń (cto). Wynikowe pliki .cto są takie same jak te, które są tworzone przy użyciu kompilatora tabeli poleceń (CTC) do kompilowania plików konfiguracyjnych .ctc. Jednak pliki vsct oparte na XML mają pewne zalety, takie jak edytor XML i XML IntelliSense.

 Aby dowiedzieć się więcej o składni i semantyki plików vsct, zobacz [Projektowanie tabeli poleceń XML (. Vsct) Pliki](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>W tej sekcji
 [Projektowanie tabeli poleceń XML (pliki Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 W tym artykule opisano sposób projektowania plików vsct.

 [Instrukcje: tworzenie pliku Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Porównuje metody tworzenia pliku vsct. W tym artykule opisano proces ręcznego tworzenia nowego pliku vsct.

## <a name="related-sections"></a>Sekcje pokrewne
 [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Zawiera szczegółowe informacje o każdej sekcji pliku konfiguracyjnego XML tabeli poleceń.

 [Konfiguracja tabeli poleceń (. Ctc) Pliki](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c) przedstawia przegląd przestarzałego formatu pliku ctc.

 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Zawiera opis specyfikacji formatu tabeli poleceń.

 [Zasoby w pakietach VSPackage](../../extensibility/internals/resources-in-vspackages.md)

 W tym artykule opisano sposób korzystania z zasobów zarządzanych i niezarządzanych w zarządzanych pakietach VSPackages.

 [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)

 W tym artykule wyjaśniono, jak utworzyć interfejs użytkownika zawierający menu, paski narzędzi i pola kombi poleceń.

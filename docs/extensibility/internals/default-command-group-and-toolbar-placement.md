---
title: Ustawienie polecenia domyślnego, grupowania i paska narzędzi | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b432b514231e876dda1393bad8a315030272d998
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708891"
---
# <a name="default-command-group-and-toolbar-placement"></a>Domyślne rozmieszczenie polecenia, grupy i paska narzędzi
Aby uzyskać jednolitość i stabilność produktu, interfejs użytkownika [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] domyślnie wyświetla niektóre grupy poleceń i zawiera definicje poleceń i grup poleceń. VsPackages można również używać standardowych poleceń i grup poleceń.

 Domyślne grupy poleceń dzielą się na trzy kategorie: polecenia IDE, polecenia produktu i polecenia edytora.

## <a name="default-ide-commands"></a>Domyślne polecenia IDE
 Domyślny pasek narzędzi IDE zawiera polecenia udostępnione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]przez wszystkie produkty zawarte w programie . Należą do nich polecenia odnoszące się do ogólnych operacji projektu, takich jak **polecenie Zapisz** i Polecenie **Dodaj element.** VsPackages nie należy dodawać lub odejmować od tego paska narzędzi, z jednym wyjątkiem: Jeśli produkt lub VSPackage dodaje nowe okno narzędzia, a następnie okno powinno zostać dodane do listy dostępnych okien narzędzi w menu **Widok.** Nowe produkty lub VSPackages można dodać własny pasek narzędzi.

## <a name="default-product-commands"></a>Domyślne polecenia produktu
 Każdy produkt może dostarczyć IDE z własnym domyślnym paskiem narzędzi, który zawiera ważne i często używane polecenia. Najlepiej jest jednak używać istniejących menu i pasków narzędzi, gdy tylko jest to możliwe i uzupełnić je innymi paskami narzędzi specyficznymi dla zadania, zgodnie z potrzebami.

 Pole priorytetu dla paska narzędzi określa jego położenie wiersza. Zerowy priorytet umieszcza pasek narzędzi w trzecim wierszu (wiersz 3), pod paskiem menu (wiersz 1) i paskiem narzędzi **Standardowy** (wiersz 2). W związku z tym inne paski narzędzi są wyświetlane w wierszu (priorytet + 3). Kolejne paski narzędzi są umieszczane w tym samym wierszu, jeśli jest miejsce; w przeciwnym razie są one automatycznie przenoszone do następnego wiersza.

## <a name="default-editor-commands"></a>Domyślne polecenia edytora
 VsPackage, który zapewnia edytor niestandardowy powinien zapewnić domyślny pasek narzędzi, który zawiera najważniejsze i często używane polecenia w tym edytorze. Pasek narzędzi edytora powinien pojawić się, gdy edytor jest aktywny i powinien być ukryty, gdy edytor nie jest aktywny. Ta widoczność jest `VisibilityConstraints` kontrolowana w elemencie pliku *vsct.*

 Paski narzędzi edytora powinny być umieszczone poniżej IDE i paski narzędzi produktu.

## <a name="see-also"></a>Zobacz też
- [Polecenia, menu i grupy zdefiniowane przez IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Jak vspackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

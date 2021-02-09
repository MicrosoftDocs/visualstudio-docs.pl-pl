---
title: Domyślne położenie poleceń, grup i pasków narzędzi | Microsoft Docs
description: Dowiedz się więcej na temat poleceń IDE, poleceń produktów i poleceń edytora, które domyślnie są wyświetlane w interfejsie użytkownika programu Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1c38abc09b0d5c8996cde44d33f4778a54a0cd62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902961"
---
# <a name="default-command-group-and-toolbar-placement"></a>Domyślne położenie poleceń, grup i pasków narzędzi
W celu zapewnienia jednorodności i stabilności produktu interfejs użytkownika domyślnie wyświetla pewne grupy poleceń i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawiera definicje poleceń i grup poleceń. Pakietów VSPackage może również używać standardowych poleceń i grup poleceń.

 Domyślne grupy poleceń dzielą się na trzy kategorie: polecenia środowiska IDE, polecenia produktów i polecenia edytora.

## <a name="default-ide-commands"></a>Domyślne polecenia środowiska IDE
 Domyślny pasek narzędzi IDE zawiera polecenia udostępniane przez wszystkie produkty zawarte w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Obejmują one polecenia dotyczące ogólnych operacji projektu, takich jak polecenie **Zapisz** i polecenie **Dodaj element** . Pakietów VSPackage nie powinna dodawać ani odejmować z tego paska narzędzi, z wyjątkiem jednego wyjątku: Jeśli produkt lub pakietu VSPackage dodaje nowe okno narzędzi, to okno należy dodać do listy dostępnych okien narzędzi w menu **Widok** . Nowe produkty lub pakietów VSPackage mogą dodawać własne paski narzędzi.

## <a name="default-product-commands"></a>Domyślne polecenia produktu
 Każdy produkt może zapewnić środowisko IDE z własnym domyślnym paskiem narzędzi zawierającym ważne i często używane polecenia. Najlepszym rozwiązaniem jest jednak używanie istniejących menu i pasków narzędzi, gdy jest to możliwe, a także uzupełnienie ich przy użyciu innych pasków narzędzi specyficznych dla zadań.

 Pole priorytet dla paska narzędzi określa położenie wiersza. Zero priorytecie umieszcza pasek narzędzi w trzecim wierszu (wiersz 3), pod paskiem menu (wiersz 1) i **standardowym** paskiem narzędzi (wiersz 2). W związku z tym inne paski narzędzi są wyświetlane w wierszu (priorytet + 3). Kolejne paski narzędzi są umieszczane w tym samym wierszu, w przypadku których występuje pomieszczenie; w przeciwnym razie są one automatycznie przenoszone do następnego wiersza.

## <a name="default-editor-commands"></a>Domyślne polecenia edytora
 Pakietu VSPackage z edytorem niestandardowym powinien udostępniać domyślny pasek narzędzi, który zawiera najważniejsze i często używane polecenia w tym edytorze. Pasek narzędzi edytora powinien pojawić się, gdy Edytor jest aktywny i powinien być ukryty, gdy Edytor nie jest aktywny. Widoczność jest kontrolowana w `VisibilityConstraints` elemencie pliku *. vsct* .

 Paski narzędzi edytora powinny być umieszczone poniżej pasków narzędzi IDE i produktów.

## <a name="see-also"></a>Zobacz też
- [Polecenia, menu i grupy zdefiniowane w środowisku IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

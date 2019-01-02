---
title: Domyślnie polecenia, grupy i położenie paska narzędzi | Dokumentacja firmy Microsoft
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
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d4292ff0a3760c412d0c12961ad7b34ad18f607
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850982"
---
# <a name="default-command-group-and-toolbar-placement"></a>Domyślne położenie poleceń, grup i narzędzi
Jednolitość produktu i stabilności interfejsu użytkownika niektórych grup poleceń są domyślnie wyświetlane, i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawiera definicje dla poleceń i grup poleceń. Pakietów VSPackage również używać poleceń standardowych i grup poleceń.  
  
 Domyślne grupy poleceń można podzielić na trzy kategorie: Polecenia IDE, polecenia produktu i poleceń edytora.  
  
## <a name="default-ide-commands"></a>Domyślne polecenia IDE  
 Narzędzi IDE domyślny zawiera polecenia, które współużytkowane przez wszystkie produkty zawarte w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Należą do nich poleceń związanych z operacjami ogólny projekt, takich jak **Zapisz** polecenia i **elementu Dodawanie** polecenia. Pakietów VSPackage nie należy dodać do lub odjęcia od tego paska narzędzi z jednym wyjątkiem: Jeśli produkt lub pakietu VSPackage dodaje nowe okno narzędzi, a następnie okna powinna być dodana do listy okien narzędzi dostępnych w **widoku** menu. Nowe produkty lub pakietów VSPackage można dodać własnych narzędzi.  
  
## <a name="default-product-commands"></a>Domyślne polecenia produktu  
 Każdy produkt może zapewnić środowisko IDE z narzędzi własnego domyślny, który zawiera ważne i często używanych poleceń. Najlepiej jest, jednak można użyć istniejącego menu i paski narzędzi w miarę możliwości w celu uzupełnienia ich z pasków narzędzi specyficzne dla zadania, zgodnie z potrzebami.  
  
 Pole Priorytet dla paska narzędzi określa jej położenie wiersza. Zero priorytet umieszcza paska narzędzi na trzecim wierszu (wiersz 3), poniżej paska menu (wiersz 1) i **standardowa** paska narzędzi (wiersz 2). W związku z tym, pasków narzędzi są wyświetlane w wierszu (priorytet + 3). Kolejne paski narzędzi są umieszczane w tym samym wierszu, w przypadku miejsca; w przeciwnym razie one są automatycznie przenoszone do następnego wiersza.  
  
## <a name="default-editor-commands"></a>Domyślne poleceń edytora  
 Pakietu VSPackage, który zawiera niestandardowy Edytor powinien dostarczyć domyślne paska narzędzi, który zawiera najważniejsze i często używanych poleceń w tym edytorze. Na pasku narzędzi edytora powinny być wyświetlane, gdy edytora jest aktywne i powinny być ukryte, gdy edytor jest nieaktywny. Widoczność tego jest kontrolowany w `VisibilityConstraints` elementu *vsct* pliku.  
  
 Paski narzędzi edytora powinny być umieszczane poniżej pasków narzędzi IDE i produktu.  
  
## <a name="see-also"></a>Zobacz także  
 [Polecenia definiowane w IDE, menu i grupy](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
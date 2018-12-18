---
title: Domyślnie polecenia, grupy i położenie paska narzędzi | Dokumentacja firmy Microsoft
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
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e91d535697d0e5b9402a7b7eb3bbd4559821c68a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773642"
---
# <a name="default-command-group-and-toolbar-placement"></a>Domyślne położenie poleceń, grup i pasków narzędzi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Jednolitość produktu i stabilności interfejsu użytkownika niektórych grup poleceń są domyślnie wyświetlane, i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zawiera definicje dla poleceń i grup poleceń. Pakietów VSPackage również używać poleceń standardowych i grup poleceń.  
  
 Domyślne grupy poleceń można podzielić na trzy kategorie: środowisko IDE poleceń, polecenia produktu i poleceń edytora.  
  
## <a name="default-ide-commands"></a>Domyślne polecenia IDE  
 Narzędzi IDE domyślny zawiera polecenia, które współużytkowane przez wszystkie produkty zawarte w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Należą do nich poleceń związanych z operacjami ogólny projekt, takich jak **Zapisz** polecenia i **elementu Dodawanie** polecenia. Pakietów VSPackage nie może dodać do lub odjęcia od tego paska narzędzi z jednym wyjątkiem: Jeśli produkt lub pakietu VSPackage dodaje nowe okno narzędzi, a następnie okna powinna być dodana do listy okien narzędzi dostępnych w **widoku** menu. Nowe produkty lub pakietów VSPackage można dodać własnych narzędzi.  
  
## <a name="default-product-commands"></a>Domyślne polecenia produktu  
 Każdy produkt może zapewnić środowisko IDE z narzędzi własnego domyślny, który zawiera ważne i często używanych poleceń. Najlepiej jest, jednak można użyć istniejącego menu i paski narzędzi w miarę możliwości w celu uzupełnienia ich z pasków narzędzi specyficzne dla zadania, zgodnie z potrzebami.  
  
 Pole Priorytet dla paska narzędzi określa jej położenie wiersza. Zero priorytet umieszcza paska narzędzi na trzecim wierszu (wiersz 3), poniżej paska menu (wiersz 1) i **standardowa** paska narzędzi (wiersz 2). W związku z tym, pasków narzędzi są wyświetlane w wierszu (priorytet + 3). Kolejne paski narzędzi są umieszczane w tym samym wierszu, w przypadku miejsca; w przeciwnym razie one są automatycznie przenoszone do następnego wiersza.  
  
## <a name="default-editor-commands"></a>Domyślne poleceń edytora  
 Pakietu VSPackage, który zawiera niestandardowy Edytor powinien dostarczyć domyślne paska narzędzi, który zawiera najważniejsze i często używanych poleceń w tym edytorze. Na pasku narzędzi edytora powinny być wyświetlane, gdy edytora jest aktywne i powinny być ukryte, gdy edytor jest nieaktywny. Widoczność tego jest kontrolowany w `VisibilityConstraints Element` pliku vsct.  
  
 Paski narzędzi edytora powinny być umieszczane poniżej pasków narzędzi IDE i produktu.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia definiowane w IDE, menu i grupy](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)


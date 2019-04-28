---
title: Opinia dla użytkownika | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7773c611733ccec525fc25264311e72c1dfe36e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62537683"
---
# <a name="feedback-to-the-user"></a>Opinia dla użytkownika
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE), wizualną opinię dotyczący możliwości opiera się na bieżące zaznaczenie i kontekst zaznaczenia globalnego użytkownika. W poniższej tabeli wymieniono funkcje, które są dostępne w kontekstach inną opcję.  
  
|Kontekst zaznaczenia|Dostępne funkcje|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|Bieżący zestaw produktów|Specyficzne dla produktu|  
|Aktywnej hierarchii|Określonego typu hierarchii|  
|Element aktywnej hierarchii|Określonego typu elementu w hierarchii|  
|Aktywnego dokumentu|Określonego typu dokumentu|  
|Okno najwyższego poziomu interfejsu wielu dokumentów (MDI)|Określonego typu okno|  
|Bieżący kontekst zaznaczenia|Określone kontekst zaznaczenia|  
  
 Jeśli tylko urządzenia surface funkcjonalność, użytkownicy muszą i zapewnić spójne wybór i opinie kontekst środowiska można zmniejszyć złożoność w środowisku IDE. Przy każdym otwarciu okna w IDE, stosowane są następujące reguły:  
  
- Jeśli okno zmienia kontekst zaznaczenia, informacje zwrotne dotyczące wyboru jest wyraźnie wskazane w oknie i dynamiczna Pomoc okna, jeśli wyświetlony, jest zaktualizowana w celu odzwierciedlenia bieżącego kontekstu.  
  
- Jeśli okno zmienia kontekst zaznaczenia globalnego, wszystkich menu kontekstowych, okna aktywnej hierarchii i na pasku tytułu aplikacji są aktualizowane, tak aby odzwierciedlić bieżący kontekst.  
  
- Okno powinno powierzchni właściwości dla bieżącego zaznaczenia w **właściwości** okna i, opcjonalnie, jeśli wyświetlony, **strony właściwości** okno dialogowe.  
  
- Jeśli okno nie powierzchni właściwości lub zmienić kontekst zaznaczenia globalnego, informacje zwrotne dotyczące wyboru nie powinna pozostać w oknie, gdy nie jest już aktywnego okna w IDE.  
  
- Wszystkie okna narzędzi specyficznych dla dokumentu stale powinny odzwierciedlać aktywnego dokumentu.  
  
- Menu, paski narzędzi i paska tytułu aplikacji powinny odzwierciedlać okna klienta znajdujące się najwyżej interfejsu wielu dokumentów (MDI).  
  
  Na przykład po otwarciu widoku HTML w formularzu sieci Web w projekcie aplikacji sieci Web w języku Visual Basic i użytkownik wybierze `<td>` tagu, informacje są przekazywane w następujący sposób:  
  
- Wybór jest wskazane w aktywnym oknie i zostaną uwzględnione w **właściwości** okna.  
  
- Specyficzne dla dokumentu **przybornika** zostanie zaktualizowany w celu odzwierciedlenia aktywnego dokumentu.  
  
- **Edytora** narzędzi i **tabeli** są wyświetlane w menu i na pasku tytułu aktualizowany w celu odzwierciedlenia okna formularza sieci Web.  
  
- Okno aktywnej hierarchii, które jest zazwyczaj **Eksploratora rozwiązań**i jej aktualizacji paska tytułu, aby odzwierciedlić bieżący kontekst i kontekstowej **projektu** poleceń menu teraz je zastosować do aktywnego internetowego Projekt aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md)   
 [Hierarchie i wybór](../../extensibility/internals/hierarchies-and-selection.md)

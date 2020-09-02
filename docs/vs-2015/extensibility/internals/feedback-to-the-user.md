---
title: Opinie do użytkownika | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537683"
---
# <a name="feedback-to-the-user"></a>Opinia dla użytkownika
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE), opinie wizualne dotyczące dostępnych funkcji opierają się na bieżącym wyborze użytkownika i globalnym kontekście wyboru. W poniższej tabeli wymieniono funkcje dostępne w różnych kontekstach wyboru.  
  
|Kontekst zaznaczenia|Dostępna funkcja|  
|-----------------------|-----------------------------|  
|IDE|Globalnie|  
|Bieżący zestaw produktów|Specyficzne dla produktu|  
|Aktywna hierarchia|Specyficzne dla typu hierarchii|  
|Element aktywnej hierarchii|Specyficzne dla typu elementu hierarchii|  
|Aktywny dokument|Specyficzne dla typu dokumentu|  
|Okno interfejsu wielu dokumentów (MDI)|Specyficzne dla typu okna|  
|Bieżący kontekst zaznaczenia|Specyficzne dla kontekstu wyboru|  
  
 Jeśli tylko chcesz, aby użytkownicy mieli potrzebną funkcjonalność i stale dostarczali spójny wybór i informacje dotyczące kontekstu środowiska, zmniejsz złożoność w IDE. Następujące reguły mają zastosowanie przy każdym otwarciu okna w środowisku IDE:  
  
- Jeśli okno zmieni kontekst zaznaczenia, opinia o wyborze jest jasno wskazana w oknie, a dynamiczne okno pomocy, jeśli jest wyświetlany, zostanie zaktualizowane w celu odzwierciedlenia bieżącego kontekstu.  
  
- Jeśli okno zmieni kontekst zaznaczenia globalnego, wszystkie menu specyficzne dla kontekstu, okno aktywnej hierarchii i pasek tytułu aplikacji są aktualizowane w celu odzwierciedlenia bieżącego kontekstu.  
  
- Okno powinno mieć właściwości powierzchni dla bieżącego zaznaczenia w oknie **Właściwości** i opcjonalnie, jeśli jest wyświetlany, okno dialogowe **strony właściwości** .  
  
- Jeśli okna nie są właściwościami powierzchni ani nie zmieniają globalnego kontekstu wyboru, opinia o wyborze nie powinna pozostać w oknie, gdy nie jest już aktywnym oknem w IDE.  
  
- Wszystkie okna narzędzi specyficzne dla dokumentu powinny stale odzwierciedlać aktywny dokument.  
  
- Menu, paski narzędzi i pasek tytułu aplikacji powinny odzwierciedlać okno klienta interfejsu wielu dokumentów (MDI).  
  
  Na przykład gdy zostanie otwarty widok HTML formularza sieci Web w ramach projektu aplikacji sieci Web Visual Basic, a użytkownik wybierze `<td>` znacznik, opinia będzie dostarczana w następujący sposób:  
  
- Zaznaczenie jest zaznaczone w aktywnym oknie i odzwierciedlone w oknie **Właściwości** .  
  
- **Przybornik** specyficzny dla dokumentu zostanie zaktualizowany w celu odzwierciedlenia aktywnego dokumentu.  
  
- Zostanie wyświetlony pasek narzędzi **edytora** i menu **tabela** , a pasek tytułu zostanie zaktualizowany w celu odzwierciedlenia okna formularza sieci Web.  
  
- Aktywne okno hierarchii, które jest zwykle **Eksplorator rozwiązań**, a jego pasek tytułu jest aktualizowany w celu odzwierciedlenia bieżącego kontekstu i poleceń menu **projektu** kontekstowego, teraz stosuje się do projektu aktywnej aplikacji sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybór i waluta w IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Obiekty kontekstu wyboru](../../extensibility/internals/selection-context-objects.md)   
 [Hierarchie i wybór](../../extensibility/internals/hierarchies-and-selection.md)

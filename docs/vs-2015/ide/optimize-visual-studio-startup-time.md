---
title: Optymalizowanie czasu uruchamiania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0ceed13cc320e2c98d413e6694acb2b473ad72eb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780278"
---
# <a name="optimize-visual-studio-startup-time"></a>Optymalizowanie czasu uruchamiania programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W idealnym przypadku programu Visual Studio powinna zawsze uruchamiać tak szybko, jak to możliwe. Jednak rozszerzenia programu Visual Studio i Otwórz okna może niekorzystnie wpłynąć na czas uruchamiania, ponieważ są one ładowane automatycznie podczas uruchamiania. **Zarządzanie wydajnością programu Visual Studio** okna umożliwia nie tylko sprawdzać, które rozszerzenia i funkcje mają wpływ na czas uruchamiania programu Visual Studio, ale również umożliwia określenie ich zachowanie ładowania, dzięki czemu masz większą kontrolę nad jak szybko Uruchamiania programu Visual Studio.

## <a name="control-startup-behavior"></a>Zachowanie podczas uruchamiania kontrolki

Aby uniknąć rozszerzanie czas uruchamiania, Visual Studio 2017 pozwala uniknąć ładowanie rozszerzeń podczas uruchamiania przy użyciu podejścia na żądanie — obciążenia. Oznacza to, że rozszerzenia nie otwieraj natychmiast po zakończeniu programu Visual Studio uruchamia, ale raczej Otwórz asynchronicznie na zgodnie z potrzebami po uruchomieniu. Ponadto ponieważ okien narzędzi pozostawione otwarte w poprzedniej sesji programu Visual Studio może zmniejszyć czas uruchamiania, Visual Studio otwiera okien narzędzi w sposób bardziej inteligentne, aby uniknąć wpływu na czas uruchamiania.

Jeśli program Visual Studio wykryje powolne uruchamiania, pojawi się komunikat podręczny, wysyłać alerty o oknie rozszerzenia lub narzędzia, które jest przyczyną spowolnienia. Komunikat zawiera również link do **zarządzanie wydajnością programu Visual Studio** okno dialogowe, które wyświetla okna narzędzia i rozszerzenia, które mają wpływ na wydajność uruchamiania. To okno dialogowe umożliwia zmianę rozszerzenia i narzędzia Ustawienia okna, aby zwiększyć wydajność uruchamiania.

![Zarządzanie wydajnością programu Visual Studio — okno podręczne](../ide/media/vside-perfdialog-popup.PNG "zarządzanie wydajnością programu Visual Studio — okno podręczne")

**Zarządzanie wydajnością programu Visual Studio** okno dialogowe ma dwie kategorie: **Rozszerzenia** i **narzędzia Windows**.

### <a name="control-extensions"></a>Rozszerzenia formantów
Jeśli rozszerzenie spowalnia uruchamiania programu Visual Studio, rozszerzenie pojawia się w **okna dialogowego Zarządzanie wydajnością programu Visual Studio** po wybraniu jednego z typów rozszerzeń. Jeśli negatywny wpływ na czas uruchamiania (która znajduje się w obszarze **wpływ** sekcji) jest zbyt wysoka, użytkownik może zawsze wyłączyć rozszerzenie podczas uruchamiania, wybierając **wyłączyć** przycisk. Można ponownie włączyć rozszerzenie dla przyszłych sesji, korzystając z Menedżera rozszerzeń lub w oknie dialogowym Zarządzanie wydajnością programu Visual Studio.

![Zarządzanie wydajnością programu Visual Studio — rozszerzenia](../ide/media/vside-perfdialog-extensions.PNG "zarządzanie wydajnością programu Visual Studio — rozszerzenia")

Oprócz rozszerzenia uruchamiania można również wyłączyć rozszerzenia, które są ładowane podczas ładowania rozwiązania, lub gdy użytkownik wpisuje. Po prostu wybierz scenariusz, który umożliwia wyświetlenie listy skojarzonych rozszerzeń.

### <a name="control-tool-windows"></a>Formant okna narzędzi
Okno narzędzia spowalnia uruchamiania programu Visual Studio, możesz pozostawić jej zachowanie domyślne (dzięki czemu umożliwia żadnych korzyści w szybkość uruchamiania), czy jego zachowanie można zastąpić, wybierając jedną z dwóch zachowań:

- **Nie pokazuj okna przy uruchamianiu:** Jeśli ta opcja jest wybrana, oknie określonego narzędzia będzie zawsze można zamknąć po otwarciu programu Visual Studio, nawet wtedy, gdy otwarte w poprzedniej sesji. Możesz otworzyć okno narzędzia w menu.
- **Automatycznie Ukryj okno przy uruchamianiu:** Jeśli okno narzędzia zostało pozostawione otwarte w poprzedniej sesji, wybranie tej opcji spowoduje Zwiń grupę okna narzędzi przy uruchamianiu w w celu uniknięcia Inicjowanie okna narzędzia. Jest to dobre rozwiązanie, korzystając z okna narzędzia często, ponieważ okna narzędzi jest nadal dostępna, ale nie będzie miało negatywny wpływ na czas uruchamiania programu Visual Studio.

![Zarządzanie wydajnością programu Visual Studio — okien narzędzi](../ide/media/vside-perfdialog-toolwindows.PNG "zarządzanie wydajnością programu Visual Studio — okna narzędzi")

Jeśli później zmieni zdanie, możesz przywrócić żadnej z tych opcji w **zarządzanie wydajnością programu Visual Studio** okno dialogowe. Aby otworzyć **zarządzanie wydajnością programu Visual Studio** okno dialogowe, na pasku menu wybierz **pomocy**, **zarządzanie wydajnością programu Visual Studio**.

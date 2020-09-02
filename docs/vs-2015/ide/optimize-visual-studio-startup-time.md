---
title: Optymalizowanie czasu uruchamiania | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f00bbc7741768852b5928b249dc7035bc440992
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670398"
---
# <a name="optimize-visual-studio-startup-time"></a>Optymalizowanie czasu uruchamiania programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W idealnym przypadku program Visual Studio powinien zawsze być uruchamiany jak najszybciej. Jednak rozszerzenia programu Visual Studio i otwarte okna narzędzi mogą niekorzystnie wpłynąć na czas uruchamiania, ponieważ ładują się automatycznie podczas uruchamiania. Okno **Zarządzaj wydajnością programu Visual Studio** umożliwia nie tylko sprawdzenie, które rozszerzenia i funkcje mają wpływ na czas uruchamiania programu Visual Studio, ale również pozwala określić zachowanie ładowania, dzięki czemu masz większą kontrolę nad sposobem uruchamiania programu Visual Studio.

## <a name="control-startup-behavior"></a>Sterowanie zachowaniem uruchamiania

Aby uniknąć wydłużenia czasu uruchamiania, program Visual Studio 2017 i nowsze unikają ładowania rozszerzeń podczas uruchamiania przy użyciu podejścia na żądanie. Oznacza to, że rozszerzenia nie otwierają się natychmiast po uruchomieniu programu Visual Studio, ale zamiast tego należy otwierać je asynchronicznie w zależności od potrzeb po uruchomieniu. Ponadto, ponieważ okna narzędzi otwierane w poprzedniej sesji programu Visual Studio mogą spowalniać uruchamianie, program Visual Studio otwiera okna narzędzi w bardziej inteligentny sposób, aby uniknąć wpływu na czas uruchamiania.

Jeśli program Visual Studio wykryje wolne uruchomienie, zostanie wyświetlony komunikat podręczny z powiadomieniem o rozszerzeniu lub oknie narzędzi, które powoduje spowolnienie. Komunikat zawiera również link do okna dialogowego **Zarządzanie wydajnością programu Visual Studio** , w którym znajduje się lista rozszerzeń i narzędzi systemu Windows, które mają wpływ na wydajność uruchamiania. To okno dialogowe pozwala zmienić ustawienia rozszerzenia i okna narzędzi, aby zwiększyć wydajność uruchamiania.

![Zarządzanie wydajnością programu Visual Studio — menu podręczne](../ide/media/vside-perfdialog-popup.PNG "Zarządzanie wydajnością programu Visual Studio — menu podręczne")

Okno dialogowe **Zarządzanie wydajnością programu Visual Studio** ma dwie kategorie: **rozszerzenia** i **okna narzędzi**.

### <a name="control-extensions"></a>Rozszerzenia formantów
Jeśli rozszerzenie spowalnia Uruchamianie programu Visual Studio, rozszerzenie pojawia się w **oknie dialogowym Zarządzaj wydajnością programu Visual Studio** w przypadku wybrania jednego z typów rozszerzeń. Jeśli wpływ na czas uruchamiania (który jest wymieniony w sekcji **wpływ** ) jest nieakceptowalny na wysokim poziomie, możesz wybrać opcję Zawsze wyłączaj rozszerzenie podczas uruchamiania, wybierając przycisk **Wyłącz** . Można ponownie włączyć rozszerzenie dla przyszłych sesji za pomocą Menedżera rozszerzeń lub okna dialogowego Zarządzanie wydajnością programu Visual Studio.

![Zarządzanie rozszerzeniami wydajności programu Visual Studio](../ide/media/vside-perfdialog-extensions.PNG "Zarządzanie rozszerzeniami wydajności programu Visual Studio")

Oprócz rozszerzeń uruchamiania, można również wyłączyć rozszerzenia, które są ładowane podczas ładowania rozwiązań lub gdy użytkownik wpisze typy. Po prostu wybierz scenariusz, aby wyświetlić listę skojarzonych rozszerzeń.

### <a name="control-tool-windows"></a>Okna narzędzi kontroli
Jeśli okno narzędzia spowalnia Uruchamianie programu Visual Studio, można wybrać opcję pozostawienia go w domyślnym zachowaniu (bez czerpania korzyści z szybkości uruchamiania) lub można przesłonić swoje zachowanie, wybierając jedno z dwóch zachowań:

- **Nie pokazuj okna przy uruchamianiu:** W przypadku wybrania tej opcji wybrane okno narzędzi będzie zawsze zamykane po otwarciu programu Visual Studio, nawet jeśli zostanie otwarte w poprzedniej sesji. Możesz otworzyć okno narzędzia z menu.
- **Automatycznie Ukryj okno przy uruchamianiu:** Jeśli okno narzędzi zostało otwarte w poprzedniej sesji, wybranie tej opcji spowoduje zwinięcie grupy okna narzędzia przy uruchamianiu, aby uniknąć inicjalizacji okna narzędzi. Jest to dobry wybór w przypadku częstego używania okna narzędzi, ponieważ okno narzędzi jest nadal dostępne, ale nie ma już negatywnego wpływu na czas uruchamiania programu Visual Studio.

![Zarządzanie wydajnością programu Visual Studio — okna narzędzi](../ide/media/vside-perfdialog-toolwindows.PNG "Zarządzanie wydajnością programu Visual Studio — okna narzędzi")

Jeśli później zmienisz zdanie, możesz przywrócić dowolną z tych opcji w oknie dialogowym **Zarządzanie wydajnością programu Visual Studio** . Aby otworzyć okno dialogowe **Zarządzanie wydajnością programu Visual Studio** , na pasku menu wybierz **Pomoc**, **Zarządzaj wydajnością programu Visual Studio**.

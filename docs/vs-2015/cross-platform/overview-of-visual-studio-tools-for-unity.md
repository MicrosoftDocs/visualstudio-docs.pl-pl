---
title: Przegląd Visual Studio Tools for Unity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: overview
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 6
ms.author: crdun
manager: crdun
ms.openlocfilehash: ba5447301c3a5581d35825ed91c17b3c9f50015f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74298751"
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Omówienie narzędzi Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji dowiesz się więcej o funkcjach Visual Studio Tools for Unity ofertach i sposobach ich użycia, aby zwiększyć produktywność przy użyciu aparatu Unity.  
  
 Za pomocą Visual Studio Tools for Unity (*rozszerzenia VSTU*) można używać programu Visual Studio do zapisywania skryptów gier i edytorów w języku C#, a następnie używać swojego zaawansowanego debugera do znajdowania i naprawiania błędów. Najnowsza wersja rozszerzenia VSTU zawiera kolorowanie składni dla języka modułu cieniującego ShaderLab środowiska Unity, lepsze wizualizacje debugera i ulepszone generowanie kodu dla kreatora z zachowaniem zachowań. ROZSZERZENIA VSTU również udostępnia pliki projektu Unity, komunikaty konsoli i możliwość uruchamiania gry w programie Visual Studio, dzięki czemu można poświęcać mniej czasu na przełączanie do i z edytora Unity podczas pisania kodu.  
  
 Kontynuuj odczytywanie, aby dowiedzieć się więcej o tych funkcjach.  
  
## <a name="integration-with-unity"></a>Integracja z programem Unity  
 Visual Studio Tools for Unity nie może być lepszym wzrostem produktywności, jeśli trzeba przełączać się między edytorem Unity a programem Visual Studio przez cały czas. Dlatego Visual Studio Tools for Unity ułatwiają wykonywanie zadań bez opuszczania programu Visual Studio.  
  
- **Eksplorator projektów środowiska Unity** wyświetla cały projekt aparatu Unity w programie Visual Studio przy użyciu tej samej hierarchii, która jest wyświetlana w edytorze aparatu Unity.  
  
- Integracja z konsolą aparatu Unity wyświetla dane wyjściowe z konsoli aparatu Unity bezpośrednio wewnątrz okna błędu programu Visual Studio.  
  
- Rozpocznij debugowanie gry z poziomu programu Visual Studio — nie musisz przełączać się z powrotem do aparatu Unity, po prostu naciśnij klawisz F5.  
  
## <a name="superior-debugging"></a>Doskonałe debugowanie  
 Połącz zaawansowany debuger programu Visual Studio z grą aparatu Unity, aby debugować skrypty i biblioteki DLL w języku C# niezależnie od tego, czy działa autonomicznie, czy w edytorze Unity. Możesz użyć wszystkich funkcji debugowania, których oczekujesz od programu Visual Studio.  
  
- Punkty przerwania, w tym warunkowe punkty przerwania.  
  
- Oceń złożone wyrażenia w okno wyrażeń kontrolnych.  
  
- Sprawdzanie i modyfikowanie wartości zmiennych i argumentów.  
  
- Przechodzenie do szczegółów obiektów złożonych i struktur danych.  
  
  Możesz nawet debugować grę Unity, gdy działa ona na innym komputerze w sieci.  
  
## <a name="productivity"></a>Produktywność  
 Oprócz wydajności tworzenia i refaktoryzacji kodu w języku C# w programie Visual Studio Visual Studio Tools for Unity udostępnia dodatkowe funkcje produktywności dla deweloperów aparatu Unity.  
  
- Kolorowanie składni dla języka ShaderLab środowiska Unity pomaga w wykorzystaniu błędów w cieniowaniu, zanim staną się usterkami. Po prostu otwórz pliki ShaderLab w programie Visual Studio.  
  
- Kreator z niezachowaniem pozwala przeglądać listę zachowań aparatu Unity i tworzy kod standardowy dla zachowań, które mogą nie być znane. Naciśnij klawisze CTRL + SHIFT + M.  
  
- Po zapoznaniu się z najczęściej używanymi zachowaniami aparatu Unity, Kreator szybkiego działania łączy je bezpośrednio na wyręką. Naciśnij kombinację klawiszy CTRL + ALT + Q.  
  
- Dostęp do dokumentacji aparatu Unity w programie Visual Studio. Po prostu Wyróżnij wywołanie interfejsu API, które chcesz poznać, a następnie naciśnij klawisze CTRL + ALT + M, CTRL + H.  
  
- Uzyskuj dostęp do wszystkich tych funkcji i nie tylko za pomocą skrótów klawiaturowych.  
  
## <a name="visual-studio-tools-for-unity-api"></a>Interfejs API programu Visual Studio Tools for Unity  
 Dostosuj i zwiększ zachowanie Visual Studio Tools for Unity przy użyciu podanych interfejsów API.  
  
- Visual Studio Tools for Unity rejestruje wywołanie zwrotne dziennika, dzięki czemu może przesyłać strumieniowo konsolę aparatu Unity do programu Visual Studio. Jeśli masz skrypty edytora, które rejestrują informacje, możesz je podłączyć do tego samego wywołania zwrotnego, aby wysyłać wiadomości do programu Visual Studio. Aby uzyskać więcej informacji, zobacz przykład wywołania zwrotnego dziennika.  
  
- Można zmienić sposób, w jaki Visual Studio Tools for Unity generuje pliki projektu przy użyciu wywołania zwrotnego stylu aparatu Unity ProjectFileGeneration. Aby uzyskać więcej informacji, zobacz przykład tworzenia pliku projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Strona główna środowiska Unity](https://unity.com/)

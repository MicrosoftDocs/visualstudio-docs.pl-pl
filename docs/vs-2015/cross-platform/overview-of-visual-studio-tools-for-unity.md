---
title: Omówienie programu Visual Studio Tools for Unity | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: overview
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 6
ms.author: crdun
manager: crdun
ms.openlocfilehash: 27ef5a1f79b97a5be5583917f1c9703b3d624c16
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68183308"
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Omówienie narzędzi Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji możesz dowiesz się więcej o funkcjach programu Visual Studio Tools dla aparatu Unity oferuje i jak można je stają się bardziej produktywne przy użyciu aparatu Unity.  
  
 Program Visual Studio Tools for Unity (*VSTU*), można użyć programu Visual Studio tworzyć gry i Edytor skrypty w języku C#, a następnie użyć jej zaawansowany debuger, można znaleźć i naprawić błędy. Najnowsza wersja narzędzi vstu zapewnia kolorowania dla języka programu do cieniowania ShaderLab mechanizmu Unity, lepszą obsługę wizualizacji debugera i ulepszone generowanie kodu dla Kreatora MonoBehavior. Narzędzia VSTU także niesie plików projektu środowiska Unity, komunikaty konsoli i możliwości, aby rozpocząć tworzenie gry w programie Visual Studio, dzięki czemu spędzisz mniej czasu przełączanie z edytora środowiska Unity podczas pisania kodu.  
  
 Kontynuuj czytanie, aby dowiedzieć się więcej o tych funkcjach.  
  
## <a name="integration-with-unity"></a>Integracja z użyciem aparatu Unity  
 Visual Studio Tools for Unity w takich sytuacjach przydałaby się wzmacniacz produktywność, gdyby trzeba było przełączać się między Edytor platformy Unity i programu Visual Studio przez cały czas. Dlatego właśnie program Visual Studio Tools for Unity ułatwia nadal wykonując pracę bez opuszczania programu Visual Studio.  
  
- **Eksploratora projektów aparatu Unity** cały projekt środowiska Unity w programie Visual Studio przy użyciu tej samej hierarchii, które są wyświetlane w Edytor platformy Unity.  
  
- Integracja z konsoli Unity wyświetla dane wyjściowe z konsoli Unity bezpośrednio w oknie błędów programu Visual Studio.  
  
- Rozpocznij debugowanie swoją grę z programu Visual Studio — nie trzeba przejdź z powrotem do środowiska Unity, wystarczy nacisnąć klawisz F5.  
  
## <a name="superior-debugging"></a>Lepsze funkcje debugowania  
 Zaawansowany debuger programu Visual Studio należy nawiązać swoją grę Unity do debugowania skryptów języka C# i biblioteki dll, niezależnie od tego, czy jest to aplikacja autonomiczna lub Edytor platformy Unity. Mogą używać wszystkich funkcji debugowania, których można oczekiwać od programu Visual Studio.  
  
- Punkty przerwania, w tym warunkowe punkty przerwania.  
  
- Oceniaj złożone wyrażenia w oknie czujki.  
  
- Sprawdzanie i modyfikowanie wartości zmiennych i argumentów.  
  
- Przejść do szczegółów w złożonych obiektów i struktur danych.  
  
  Swoją grę Unity można debugować nawet wtedy, gdy działa na innym komputerze w sieci.  
  
## <a name="productivity"></a>Produktywność  
 Oprócz programu Visual Studio wydajności ustanowionych pisanie i Refaktoryzacja kodu w języku C# Visual Studio Tools for Unity udostępnia funkcje dodatkowe produktywność dla deweloperów Unity.  
  
- Kolorowania dla języków ShaderLab Unity pomaga wykryć błędów w swojej programów do cieniowania, zanim staną się błędy. Po prostu otwórz pliki ShaderLab w programie Visual Studio.  
  
- Kreator MonoBehavior pozwala przeglądać listę zachowania Unity i tworzy standardowy kod dla zachowania, które może nie być zapoznać się z. Naciśnij klawisze CTRL + SHIFT + M.  
  
- Gdy użytkownicy zaznajomieni z zachowaniami Unity, których używasz najczęściej Kreatora szybkiego MonoBehavior umieszcza je w zasięgu ręki. Naciśnij klawisze CTRL + ALT + Q.  
  
- Dostęp do dokumentacji aparatu Unity w programie Visual Studio. Po prostu zaznacz wywołania interfejsu API, który chcesz Dowiedz się więcej o, a następnie naciśnij klawisze CTRL + ALT + M, CTRL + H.  
  
- Dostęp do tych funkcji i nie tylko za pomocą skrótów klawiaturowych.  
  
## <a name="visual-studio-tools-for-unity-api"></a>Narzędzia Visual Studio dla interfejsu API aparatu Unity  
 Dostosowywanie i rozszerzanie zachowanie programu Visual Studio Tools for Unity za pomocą podanego interfejsów API.  
  
- Visual Studio Tools for Unity rejestruje wywołanie zwrotne dziennika, dzięki czemu można przesłać strumieniowo konsoli Unity w programie Visual Studio. Jeśli masz skrypty edytora rejestrować informacje, można je podłączyć do tego samego wywołania zwrotnego do wysyłania wiadomości do programu Visual Studio. Aby uzyskać więcej informacji zobacz przykład wywołania zwrotnego dziennika.  
  
- Można zmienić, jak Visual Studio Tools for Unity generuje pliki projektu przy użyciu ProjectFileGeneration wywołania zwrotnego styl środowiska Unity. Aby uzyskać więcej informacji zobacz przykład Generowanie pliku projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Strona główna aparatu Unity](http://unity3d.com)

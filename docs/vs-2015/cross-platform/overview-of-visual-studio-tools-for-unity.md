---
title: Omówienie narzędzia programu Visual Studio dla unity | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: overview
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 6
ms.author: crdun
manager: crdun
ms.openlocfilehash: ba5447301c3a5581d35825ed91c17b3c9f50015f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74298751"
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Omówienie narzędzi Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji dowiesz się więcej na temat funkcji visual studio narzędzia dla unity oferuje i jak można ich używać, aby stać się bardziej wydajne z Unity.  
  
 Za pomocą programu Visual Studio Tools for Unity (*VSTU),* można użyć programu Visual Studio do pisania skryptów gier i edytorów w języku C#, a następnie użyć jego zaawansowanego debugera, aby znaleźć i naprawić błędy. Najnowsza wersja vstu zawiera kolorowanie składni dla języka shaderlab firmy Unity, lepsze wizualizacje debugera i ulepszone generowanie kodu dla kreatora MonoBehavior. VSTU przynosi również pliki projektu Unity, komunikaty konsoli i możliwość uruchomienia gry w programie Visual Studio, dzięki czemu można spędzić mniej czasu przełączania do iz Edytora Unity podczas pisania kodu.  
  
 Czytaj dalej, aby dowiedzieć się więcej o tych funkcjach.  
  
## <a name="integration-with-unity"></a>Integracja z jednością  
 Narzędzia programu Visual Studio dla unity nie będzie wzmacniacz produktywności, jeśli trzeba było przełączać się tam iz powrotem między edytorem Unity i Visual Studio przez cały czas. Dlatego visual studio tools for Unity ułatwia wykonywanie pracy bez opuszczania programu Visual Studio.  
  
- **Unity Project Explorer** wyświetla cały projekt Unity wewnątrz programu Visual Studio przy użyciu tej samej hierarchii wyświetlane w edytorze Unity.  
  
- Integracja konsoli Unity wyświetla dane wyjściowe z konsoli Unity bezpośrednio w oknie błędu programu Visual Studio.  
  
- Rozpocznij debugowanie gry z programu Visual Studio — nie trzeba przełączać się z powrotem do Unity, wystarczy nacisnąć klawisz F5.  
  
## <a name="superior-debugging"></a>Doskonałe debugowanie  
 Połącz zaawansowaną debuger visual studio do gry Unity do debugowania skryptów języka C# i bibliotek DLL, niezależnie od tego, czy jest uruchomiony autonomiczny lub w edytorze Unity. Można użyć wszystkich funkcji debugowania, których oczekujesz od programu Visual Studio.  
  
- Punkty przerwania, w tym warunkowe punkty przerwania.  
  
- Ocena złożonych wyrażeń w oknie Czujka.  
  
- Inspekcja i modyfikowanie wartości zmiennych i argumentów.  
  
- Przechodzenie do szczegółów w złożonych obiektach i strukturach danych.  
  
  Możesz nawet debugować swoją grę Unity, gdy działa na innym komputerze w sieci.  
  
## <a name="productivity"></a>Produktywność  
 Oprócz ustalonej wydajności programu Visual Studio do pisania i refaktoryzacji kodu w języku C#, Visual Studio Tools for Unity zapewnia dodatkowe funkcje produktywności dla deweloperów Unity.  
  
- Kolorowanki składni dla języka ShaderLab unity pomaga wykryć błędy w modułach cieniujących, zanim staną się one błędami. Wystarczy otworzyć pliki ShaderLab w programie Visual Studio.  
  
- Kreator MonoBehavior umożliwia przeglądanie listy zachowań Unity i tworzy standardowy kod dla zachowań, które mogą nie być zaznajomieni z. Naciśnij klawisze CTRL+SHIFT+M.  
  
- Po zapoznaniu się z zachowaniami Unity, których używasz najczęściej, Kreator szybkiego monobehaviora umieszcza je w zasięgu ręki. Naciśnij klawisze CTRL+ALT+Q.  
  
- Uzyskaj dostęp do dokumentacji unity z programu Visual Studio. Wystarczy zaznaczyć wywołanie interfejsu API, o których chcesz się dowiedzieć, a następnie naciśnij klawisze CTRL+ALT+M, CTRL+H.  
  
- Dostęp do wszystkich tych funkcji i nie tylko za pomocą skrótów klawiaturowych.  
  
## <a name="visual-studio-tools-for-unity-api"></a>Narzędzia programu Visual Studio dla interfejsu API unity  
 Dostosuj i rozszerz zachowanie programu Visual Studio Tools for Unity przy użyciu dostarczonych interfejsów API.  
  
- Narzędzia programu Visual Studio dla unity rejestruje wywołania zwrotnego dziennika, dzięki czemu można przesyłać strumieniowo konsoli Unity do programu Visual Studio. Jeśli masz skrypty edytora, które rejestrują informacje, można podłączyć je do tego samego wywołania zwrotnego, aby wysłać wiadomości do programu Visual Studio. Aby uzyskać więcej informacji, zobacz przykład wywołania zwrotnego dziennika.  
  
- Można zmienić sposób Visual Studio Tools for Unity generuje pliki projektu przy użyciu wywołania zwrotnego ProjectFileGeneration stylu Unity. Aby uzyskać więcej informacji, zobacz przykład generowania plików projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Strona główna Unity](https://unity.com/)

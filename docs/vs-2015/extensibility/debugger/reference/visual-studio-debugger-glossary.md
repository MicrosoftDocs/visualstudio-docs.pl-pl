---
title: Słownik debugera programu Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 19d82f006bb1c37981f60e1a0b2710588eb0053c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204782"
---
# <a name="visual-studio-debugger-glossary"></a>Słownik debugera programu Visual Studio
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

W zestawie SDK debugowania są stosowane poniższe warunki [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .  
  
## <a name="terms"></a>Terminologia  
 powiązany punkt przerwania  
 Streszczenie dla punktu przerwania ustawione w kodzie. Istnieje relacja jeden do jednego między punktem przerwania powiązanego a instrukcją punktu przerwania w strumieniu kodu. Gdy kody są zwalniane, powiązane punkty przerwania mogą usunąć powiązania.  
  
 przyczynowość  
 Zapewnia możliwość śledzenia logicznego wątku wykonywania w wielu wątkach fizycznych, procesach i maszynach oraz w celu odtworzenia stosu wywołań tego wątku logicznego w dowolnym punkcie okresu istnienia wątku.  
  
 kontekst kodu  
 Zapewnia abstrakcję pozycji w kodzie znanej dla aparatu debugowania. W przypadku większości architektur czasu wykonywania, kontekst kodu jest adresem w strumieniu instrukcji programu. W przypadku języków nietradycyjnych, w których kod nie może być reprezentowany przez instrukcje, kontekst kodu może być reprezentowany w inny sposób.  
  
 ścieżka kodu  
 Reprezentuje punkt wykonania w kodzie, w którym jest wykonywana gałąź lub wywołanie funkcji. Ślad stosu jest zasadniczo listą ścieżek kodu wywołania funkcji.  
  
 aparat debugowania (Niemcy)  
 Składnik, który umożliwia debugowanie architektury czasu wykonywania. Silnik debugowania działa w połączeniu z interpreterem lub systemem operacyjnym oraz zapewnia usługi debugowania, takie jak kontrola wykonywania, punkty przerwania i Obliczanie wyrażenia.  
  
 kontekst dokumentu  
 Zapewnia abstrakcję pozycji w dokumencie pliku źródłowego znanym aparatowi debugowania. W przypadku większości języków kontekst dokumentu jest pozycją w pliku źródłowym. W przypadku nietradycyjnych języków, dla których plik źródłowy może nie być tekstem, kontekst dokumentu może być reprezentowany przez inny sposób. Zobacz również *pozycja dokumentu*.  
  
 położenie dokumentu  
 Zapewnia abstrakcję pozycji w pliku źródłowym znanym IDE. W przypadku większości języków pozycja dokumentu jest pozycją w pliku źródłowym. W przypadku nietradycyjnych języków pozycja dokumentu może być reprezentowana w inny sposób. Zobacz również *kontekst dokumentu*.  
  
 błąd punktu przerwania  
 Streszczenie dla opisywania błędu w oczekującym punkcie przerwania. Punkt przerwania błędu może opisać błąd w lokalizacji oczekującego punktu przerwania, wyrażenie skojarzone z oczekującym punktem przerwania lub inne informacje, które uniemożliwiają oczekujący punkt przerwania z wiązania do lokalizacji kodu.  
  
 kontekst oceny  
 Zapewnia abstrakcję kontekstu programowania dla oceny wyrażenia. Zazwyczaj kontekst oceny jest zakresem. Podczas obliczania wyrażenia w kontekście wyrażenia, kontekst wyrażenia zawiera reguły zakresu, które pasują do punktu tworzenia. Na przykład kontekst wyrażenia utworzony w ramce stosu zapewni kontekst do oceny zmiennych lokalnych, parametrów metody, elementów członkowskich klasy (jeśli dotyczy) i zmiennych globalnych.  
  
 przechwycony wyjątek  
 Wyjątek, który jest przechwytywany przez aparat debugowania, nawet jeśli w bieżącej klatce stosu nie ma mechanizmu obsługi wyjątków.  
  
 JustMyCode  
 Koncepcja debugowania tylko kodu należącego do użytkownika i ignorowania całego kodu pośredniego, takiego jak kod systemowy — nawet jeśli kod źródłowy jest dostępny dla tego kodu systemowego.  
  
 oczekujący punkt przerwania  
 Zapewnia streszczenie dla punktów przerwania przed, w trakcie i po załadowaniu kodu oraz sposób wirtualizacji punktów przerwania. Oczekujący punkt przerwania:  
  
- Zawiera wszystkie informacje, które są konieczne do powiązania punktu przerwania z kodem w jednym lub większej liczbie programów.  
  
- Może wiązać się z wieloma lokalizacjami w jednym lub kilku programach.  
  
- Nigdy nie wiąże się z kodem.  
  
  Za każdym razem, gdy jest ładowany kod, wszystkie oczekujące punkty przerwania w programie są sprawdzane w celu sprawdzenia, czy można utworzyć powiązanie. Oczekujący punkt przerwania jest określany jako zawierający wszystkie powiązane punkty przerwania, które tworzy.  
  
  proces  
  Fizyczny proces Win32. Proces może zawierać wiele programów. Zobacz też *program*.  
  
  program  
  Pojedyncza przestrzeń nazw działająca w ramach określonej architektury czasu wykonywania. Zobacz również *proces*.  
  
  Menedżer debugowania sesji (SDM)  
  Zarządza dowolną liczbą aparatów debugowania, które debugują dowolną liczbę programów w wielu procesach na dowolnej liczbie komputerów. Na poziomie podstawowym model SDM jest multiplekserem aparatów debugowania. Ponadto model SDM zapewnia ujednolicony widok sesji debugowania do IDE.  
  
  ramka stosu  
  Reprezentuje stan obliczeń dla określonej ramki i określonego poziomu zagnieżdżonych wywołań funkcji.  
  
  wątek  
  Uogólnione koncepcje wykonywania instrukcji opartych na stosie działające w co najmniej jednym programie.  
  
  punkt przerwania ostrzeżenia  
  Streszczenie opisujące ostrzeżenie w oczekującym punkcie przerwania. Punkt przerwania ostrzegawczy opisuje powód, dla którego oczekujący punkt przerwania nie został jeszcze powiązany z lokalizacją w kodzie. Może to być spowodowane tym, że kod nie został jeszcze załadowany do lokalizacji opisanej przez oczekujący punkt przerwania lub z innego powodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)

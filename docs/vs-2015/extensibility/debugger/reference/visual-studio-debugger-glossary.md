---
title: Słownik debugera programu Visual Studio | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204782"
---
# <a name="visual-studio-debugger-glossary"></a>Słownik debugera programu Visual Studio
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Poniżej przedstawiono terminów używanych w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugowanie zestawu SDK.  
  
## <a name="terms"></a>Warunki  
 powiązany punkt przerwania  
 Ustawianie klasą abstrakcyjną dla punktu przerwania w kodzie. Istnieje bezpośredni związek pomiędzy powiązany punkt przerwania i instrukcję punkt przerwania w strumieniu kodu. Gdy kod zwalnia, powiązane punkty przerwania nie może usunąć powiązanie.  
  
 przyczynowości  
 Zapewnia możliwość śledzenia logiczne wątkiem wykonywania w wielu fizycznych wątków, procesy i maszyn oraz rekonstrukcji stosu wywołań logicznych wątek na dowolnym etapie w okresie istnienia w tym wątku.  
  
 Kontekst kodu  
 Udostępnia abstrakcję pozycji w kodzie, o których wiadomo, że aparat debugowania. Dla większości architektur środowiska wykonawczego kontekst kodu nie jest adresem w usłudze stream instrukcji programu. Nietradycyjnych języków, w których kod nie może być reprezentowany przez instrukcje, kontekst kodu mogą być reprezentowane w inny sposób.  
  
 Ścieżka kodu  
 Reprezentuje punkt wykonywania w kodzie, w którym odgałęzienia lub wykonywane jest wywołanie funkcji. Ślad stosu jest zasadniczo lista ścieżek kodu wywołania funkcji.  
  
 Aparat debugowania (DE)  
 Składnik, który umożliwia Profilowanie architektury środowiska wykonawczego. Aparat debugowania działa w połączeniu z interpreter lub systemu operacyjnego i zapewnia debugowania usług, takich jak wykonanie kontroli, punkty przerwania i wyrażenie oceny.  
  
 Kontekst dokumentu  
 Udostępnia abstrakcję do pozycji w dokumencie pliku źródłowym, wiadomo, że aparat debugowania. W przypadku większości języków kontekstu dokumentu jest pozycji w pliku źródłowym. Nietradycyjnych języków, dla których plik źródłowy nie może być tekstu, kontekstu dokumentu może być reprezentowany za pomocą innych środków. Zobacz też *pozycji dokumentu*.  
  
 Położenie dokumentu  
 Udostępnia abstrakcję pozycji w pliku źródłowym, wiadomo, że środowisko IDE. W przypadku większości języków położenie dokumentu jest pozycji w pliku źródłowym. W przypadku języków nietradycyjnych położenie dokumentu może być reprezentowany w inny sposób. Zobacz też *kontekstu dokumentu*.  
  
 Błąd punktu przerwania  
 Klasą abstrakcyjną dla opisu błędu w oczekującym punktem przerwania. Błąd punktu przerwania może opisać błąd w lokalizacji oczekującym punktem przerwania, wyrażeń związanych z Oczekujący punkt przerwania lub inne informacje, które uniemożliwia oczekujący punkt przerwania powiązania do lokalizacji kodu.  
  
 Kontekst oceny  
 Udostępnia abstrakcję programowania kontekstu do obliczenia wyrażenia. Zazwyczaj kontekst oceny jest zakresem. Podczas wykonywania oceny wyrażenia w kontekście wyrażenia, kontekst wyrażenie zawiera reguły zakresu, odpowiadające jej punkt tworzenia. Na przykład z kontekstu wyrażenia utworzone w ramce stosu zapewni kontekście ocenianie zmiennych lokalnych, parametrów metody, elementy członkowskie klasy (jeśli dotyczy) i zmiennych globalnych.  
  
 przechwycone wyjątku  
 Wyjątek, który jest przechwycony przez aparat debugowania, nawet jeśli nie mechanizm obsługi wyjątków są używane w bieżącej ramki stosu.  
  
 JustMyCode  
 Pojęcie debugowania tylko kodu, który należy do użytkownika i ignoruje wszelkie kodu pośredniego, takich jak systemu kodu — nawet jeśli kod źródłowy jest dostępny dla tego kodu systemowego.  
  
 Oczekujący punkt przerwania  
 Udostępnia abstrakcję do punktów przerwania przed, podczas i po kod jest załadowany i sposób wirtualizacji punktów przerwania. A oczekujących punktów przerwania:  
  
- Zawiera wszystkie informacje potrzebne do powiązać punkt przerwania z kodu w jednym lub wielu programów.  
  
- Może zostać powiązany z wieloma lokalizacjami kodu w jeden lub więcej programów.  
  
- Nigdy nie wiąże się z kodu.  
  
  Każdy kod w czasie ładowania, wszystkich oczekujących punktów przerwania w programie są sprawdzane w celu sprawdzenia, jeśli można powiązać. Oczekujący punkt przerwania jest nazywany ma zawierać wszystkie powiązane punkty przerwania, które powiąże.  
  
  proces  
  Proces fizyczny Win32. Proces może zawierać wiele programów. Zobacz też *program*.  
  
  program  
  Jednej przestrzeni nazw działający szczególna Architektura środowiska wykonawczego. Zobacz też *procesu*.  
  
  Menedżer debugowania sesji (SDM)  
  Zarządza dowolną liczbę aparaty debugowania debugowania dowolną liczbę programów w wielu procesach w dowolnej liczbie maszyn. Na podstawowym poziomie SDM jest multiplekser z aparatami debugowania. Ponadto SDM zapewnia spójny widok sesji debugowania środowiska IDE.  
  
  ramka stosu  
  Reprezentuje stan obliczeń na określoną ramkę i określonym poziomie zagnieżdżonych wywołań funkcji.  
  
  wątek  
  Pojęcie uogólnionego wykonywania instrukcji oparty na stosie, działające w co najmniej jeden program.  
  
  Ostrzeżenie punktu przerwania  
  Abstrakcja do opisywania ostrzeżenia w oczekującym punktem przerwania. Ostrzeżenie punktu przerwania w tym artykule opisano przyczyny, dlaczego oczekujący punkt przerwania nie została jeszcze powiązana z lokalizacji kodu. Może to być, czy kod nie załadował jeszcze do lokalizacji, w opisany przez oczekujący punkt przerwania lub innego powodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)

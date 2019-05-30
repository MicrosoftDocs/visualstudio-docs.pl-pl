---
title: Słownik debugera programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d968b5c0d18c7ba74e1bd5ea541fdfe080dc4f78
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316080"
---
# <a name="visual-studio-debugger-glossary"></a>Słownik debugera programu Visual Studio
Poniżej przedstawiono terminów używanych w [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugowanie zestawu SDK.

## <a name="terms"></a>Warunki
 powiązany punkt przerwania klasą abstrakcyjną dla punktu przerwania w kodzie. Istnieje bezpośredni związek pomiędzy powiązany punkt przerwania i instrukcję punkt przerwania w strumieniu kodu. Gdy kod zwalnia, powiązane punkty przerwania nie może usunąć powiązanie.

 przyczynowości zapewnia możliwość śledzenia logiczne wątkiem wykonywania w wielu fizycznych wątków, procesy i maszyn oraz rekonstrukcji stosu wywołań logicznych wątek na dowolnym etapie w okresie istnienia w tym wątku.

 kontekst kodu udostępnia abstrakcję pozycji w kodzie, o których wiadomo, że aparat debugowania. Dla większości architektur środowiska wykonawczego kontekst kodu nie jest adresem w usłudze stream instrukcji programu. Nietradycyjnych języków, w których kod nie może być reprezentowany przez instrukcje, kontekst kodu mogą być reprezentowane w inny sposób.

 Ścieżka kodu reprezentuje punkt wykonywania w kodzie, w którym odgałęzienia lub wykonywane jest wywołanie funkcji. Ślad stosu jest zasadniczo lista ścieżek kodu wywołania funkcji.

 Debuguj aparat (DE) A składnik, który umożliwia Profilowanie architektury środowiska wykonawczego. Aparat debugowania działa w połączeniu z interpreter lub systemu operacyjnego i zapewnia debugowania usług, takich jak wykonanie kontroli, punkty przerwania i wyrażenie oceny.

 kontekst dokumentu udostępnia abstrakcję pozycji w dokumencie pliku źródłowym, wiadomo, że aparat debugowania. W przypadku większości języków kontekstu dokumentu jest pozycji w pliku źródłowym. Nietradycyjnych języków, dla których plik źródłowy nie może być tekstu, kontekstu dokumentu może być reprezentowany za pomocą innych środków. Zobacz też *pozycji dokumentu*.

 położenie dokumentu udostępnia abstrakcję pozycji w pliku źródłowym, wiadomo, że środowisko IDE. W przypadku większości języków położenie dokumentu jest pozycji w pliku źródłowym. W przypadku języków nietradycyjnych położenie dokumentu może być reprezentowany w inny sposób. Zobacz też *kontekstu dokumentu*.

 Błąd punktu przerwania klasą abstrakcyjną dla opisu błędu w oczekującym punktem przerwania. Błąd punktu przerwania może opisać błąd w lokalizacji oczekującym punktem przerwania, wyrażeń związanych z Oczekujący punkt przerwania lub inne informacje, które uniemożliwia oczekujący punkt przerwania powiązania do lokalizacji kodu.

 kontekst oceny udostępnia abstrakcję programowania kontekstu do obliczenia wyrażenia. Zazwyczaj kontekst oceny jest zakresem. Podczas wykonywania oceny wyrażenia w kontekście wyrażenia, kontekst wyrażenie zawiera reguły zakresu, odpowiadające jej punkt tworzenia. Na przykład z kontekstu wyrażenia utworzone w ramce stosu zapewni kontekście ocenianie zmiennych lokalnych, parametrów metody, elementy członkowskie klasy (jeśli dotyczy) i zmiennych globalnych.

 przechwycony wyjątek wyjątek, który jest przechwycony przez aparat debugowania, nawet jeśli nie mechanizm obsługi wyjątków są używane w bieżącej ramki stosu.

 JustMyCode koncepcji debugowania tylko kodu, który należy do użytkownika i ignoruje wszystkie kodu pośredniego, takie jak kod systemu — nawet jeśli kod źródłowy jest dostępny dla tego kodu systemowego.

 Udostępnia abstrakcję do punktów przerwania przed, podczas i po kodzie jest realizacja oczekującego punktu przerwania załadowane oraz sposób wirtualizacji punktów przerwania. A oczekujących punktów przerwania:

- Zawiera wszystkie informacje potrzebne do powiązać punkt przerwania z kodu w jednym lub wielu programów.

- Może zostać powiązany z wieloma lokalizacjami kodu w jeden lub więcej programów.

- Nigdy nie wiąże się z kodu.

  Każdy kod w czasie ładowania, wszystkich oczekujących punktów przerwania w programie są sprawdzane w celu sprawdzenia, jeśli można powiązać. Oczekujący punkt przerwania jest nazywany ma zawierać wszystkie powiązane punkty przerwania, które powiąże.

  proces fizycznego procesu Win32. Proces może zawierać wiele programów. Zobacz też *program*.

  Program działający szczególna Architektura środowiska wykonawczego jednej przestrzeni nazw. Zobacz też *procesu*.

  Menedżer debugowania sesji (SDM) zarządza dowolną liczbę aparaty debugowania debugowania dowolną liczbę programów w wielu procesach w dowolnej liczbie maszyn. Na podstawowym poziomie SDM jest multiplekser z aparatami debugowania. Ponadto SDM zapewnia spójny widok sesji debugowania środowiska IDE.

  Ramka stosu reprezentuje stan obliczeń na określoną ramkę i określonym poziomie zagnieżdżonych wywołań funkcji.

  Wątek uogólnionego pojęcie wykonywania instrukcji oparty na stosie, działające w co najmniej jeden program.

  Ostrzeżenie punktu przerwania klasą abstrakcyjną dla opisujące ostrzeżenia w oczekującym punktem przerwania. Ostrzeżenie punktu przerwania w tym artykule opisano przyczyny, dlaczego oczekujący punkt przerwania nie została jeszcze powiązana z lokalizacji kodu. Może to być, czy kod nie załadował jeszcze do lokalizacji, w opisany przez oczekujący punkt przerwania lub innego powodu.

## <a name="see-also"></a>Zobacz także
- [Rozszerzalność debugera programu Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
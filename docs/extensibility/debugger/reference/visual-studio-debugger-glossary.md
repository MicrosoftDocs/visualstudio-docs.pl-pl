---
title: Słowniczek debugera programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 954532311fe6b63fc288877a6d41722e6ea47581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713344"
---
# <a name="visual-studio-debugger-glossary"></a>Słownik debugera programu Visual Studio
Poniżej przedstawiono terminy używane w [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugowania SDK.

## <a name="terms"></a>Warunki
 związany punkt przerwania Abstrakcja dla punktu przerwania ustawionego w kodzie. Istnieje relacja jeden do jednego między powiązanym punktem przerwania a instrukcją punktu przerwania w strumieniu kodu. Gdy kod zwalnia, powiązane punkty przerwania mogą odwiązać.

 przyczynowość Zapewnia możliwość śledzenia wątku logicznego wykonywania w wielu wątków fizycznych, procesów i maszyn i zrekonstruować stos wywołań tego wątku logicznego w dowolnym momencie w okresie istnienia tego wątku.

 kontekst kodu Zapewnia abstrakcję pozycji w kodzie znanym aparatowi debugowania. W przypadku większości architektur w czasie wykonywania kontekst kodu jest adresem w strumieniu instrukcji programu. W przypadku języków nietradycyjnych, w których kod nie może być reprezentowany przez instrukcje, kontekst kodu może być reprezentowany w inny sposób.

 ścieżka kodu reprezentuje punkt wykonania w kodzie, w którym oddział jest podejmowana lub wywoływane jest wywołanie funkcji. Śledzenie stosu jest zasadniczo lista ścieżek kodu wywołania funkcji.

 aparat debugowania (DE) Składnik, który umożliwia debugowanie architektury wykonywalnej. Aparat debugowania działa w połączeniu z interpreterem lub systemem operacyjnym i zapewnia usługi debugowania, takie jak kontrola wykonania, punkty przerwania i ocena wyrażeń.

 kontekst dokumentu Zapewnia abstrakcję pozycji w dokumencie pliku źródłowego znanego aparatowi debugowania. W przypadku większości języków kontekst dokumentu jest pozycją w pliku źródłowym. W przypadku języków nietradycyjnych, dla których plik źródłowy może nie być tekstem, kontekst dokumentu może być reprezentowany za pomocą innych środków. Zobacz też *położenie dokumentu*.

 pozycja dokumentu Zapewnia abstrakcję pozycji w pliku źródłowym znanym IDE. W przypadku większości języków pozycja dokumentu jest pozycją w pliku źródłowym. W przypadku języków nietradycyjnych pozycja dokumentu może być reprezentowana w inny sposób. Zobacz też *kontekst dokumentu*.

 punkt przerwania błędu Abstrakcja opisująca błąd w oczekującym punkcie przerwania. Punkt przerwania błędu może opisywać błąd w lokalizacji oczekującego punktu przerwania, wyrażenie skojarzone z oczekującym punktem przerwania lub inne informacje, które uniemożliwiają powiązanie oczekującego punktu przerwania z lokalizacją kodu.

 kontekst ewaluacji Zapewnia abstrakcję kontekstu programowania dla oceny wyrażenia. Zazwyczaj kontekst oceny jest zakresem. Podczas wykonywania oceny wyrażenia w kontekście wyrażenia kontekst wyrażenia zawiera reguły zakresu, które pasują do jego punktu tworzenia. Na przykład kontekst wyrażenia utworzony w ramce stosu zapewni kontekst do oceny zmiennych lokalnych, parametrów metody, elementów członkowskich klasy (jeśli dotyczy) i zmiennych globalnych.

 przechwycony wyjątek Wyjątek przechwycony przez aparat debugowania, nawet jeśli mechanizm obsługi wyjątków nie jest w miejscu w bieżącej ramce stosu.

 JustMyCode Pojęcie debugowania tylko kodu, który należy do użytkownika i ignorując cały kod pośredni, takich jak kod systemowy— nawet jeśli kod źródłowy jest dostępny dla tego kodu systemu.

 oczekujący punkt przerwania Zapewnia abstrakcję dla punktów przerwania przed, w trakcie i po załadowaniu kodu i sposobem wirtualizacji punktów przerwania. Oczekujący punkt przerwania:

- Zawiera wszystkie informacje potrzebne do powiązania punktu przerwania z kodem w jednym lub kilku programach.

- Może powiązać z wieloma lokalizacjami kodu w jednym lub kilku programach.

- Nigdy nie wiąże się z kodem.

  Za każdym razem, gdy kod się ładuje, wszystkie oczekujące punkty przerwania w programie są sprawdzane, aby sprawdzić, czy mogą one powiązać. Oczekujące punktu przerwania mówi się, że zawiera wszystkie powiązane punkty przerwania, które wiąże.

  proces Fizyczny proces Win32. Proces może zawierać wiele programów. Zobacz też *program*.

  program Pojedynczy obszar nazw działający wewnątrz określonej architektury czasu wykonywania. Zobacz też *proces*.

  menedżer debugowania sesji (SDM) Zarządza dowolną liczbą aparatów debugowania debugowania dowolną liczbę programów w wielu procesach na dowolnej liczbie komputerów. Na poziomie podstawowym SDM jest multiplekserem aparatów debugowania. Ponadto SDM zapewnia ujednolicony widok sesji debugowania do IDE.

  ramka stosu Reprezentuje stan obliczeń w określonej ramce i określony poziom wywołań funkcji zagnieżdżonych.

  wątek Uogólnione pojęcie wykonywania instrukcji opartych na stosie działa w co najmniej jednym programie.

  ostrzeżenie breakpoint Abstrakcja do opisywania ostrzeżenia w oczekującym punkcie przerwania. Punkt przerwania ostrzeżenia opisuje przyczynę, dla którego oczekujący punkt przerwania nie został jeszcze powiązany z lokalizacją kodu. Może to być, że kod nie został załadowany jeszcze dla lokalizacji opisanej przez oczekujących punktu przerwania lub z innego powodu.

## <a name="see-also"></a>Zobacz też
- [Rozszerzalność debugera programu Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)

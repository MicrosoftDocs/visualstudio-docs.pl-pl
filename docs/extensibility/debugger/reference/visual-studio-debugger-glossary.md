---
title: Słownik debugera programu Visual Studio | Microsoft Docs
description: W tym artykule opisano kilka terminów używanych w zestawie SDK debugowania programu Visual Studio, takich jak związany punkt przerwania, przyczynę i kontekst kodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1871a395e87177c89f8af2bfce640a63c2cba324
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070690"
---
# <a name="visual-studio-debugger-glossary"></a>Słownik debugera programu Visual Studio
W zestawie SDK debugowania są stosowane poniższe warunki [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

## <a name="terms"></a>Terminologia
 powiązany punkt przerwania — abstrakcję dla zestawu punktów przerwania w kodzie. Istnieje relacja jeden do jednego między punktem przerwania powiązanego a instrukcją punktu przerwania w strumieniu kodu. Gdy kody są zwalniane, powiązane punkty przerwania mogą usunąć powiązania.

 przyczynę stanowi możliwość śledzenia logicznego wątku wykonywania w wielu wątkach fizycznych, procesach i maszynach oraz w celu odtworzenia stosu wywołań tego wątku logicznego w dowolnym punkcie okresu istnienia wątku.

 kontekst kodu zawiera streszczenie położenia w kodzie znanym aparatowi debugowania. W przypadku większości architektur czasu wykonywania, kontekst kodu jest adresem w strumieniu instrukcji programu. W przypadku języków nietradycyjnych, w których kod nie może być reprezentowany przez instrukcje, kontekst kodu może być reprezentowany w inny sposób.

 ścieżka kodu reprezentuje punkt wykonania w kodzie, w którym jest wykonywana gałąź lub wywołanie funkcji. Ślad stosu jest zasadniczo listą ścieżek kodu wywołania funkcji.

 aparat debugowania (DE) składnika, który umożliwia debugowanie architektury czasu wykonywania. Silnik debugowania działa w połączeniu z interpreterem lub systemem operacyjnym oraz zapewnia usługi debugowania, takie jak kontrola wykonywania, punkty przerwania i Obliczanie wyrażenia.

 kontekst dokumentu zawiera streszczenie pozycji w dokumencie pliku źródłowego znanym aparatowi debugowania. W przypadku większości języków kontekst dokumentu jest pozycją w pliku źródłowym. W przypadku nietradycyjnych języków, dla których plik źródłowy może nie być tekstem, kontekst dokumentu może być reprezentowany przez inny sposób. Zobacz również *pozycja dokumentu*.

 Pozycja dokumentu zawiera streszczenie pozycji w pliku źródłowym znanym IDE. W przypadku większości języków pozycja dokumentu jest pozycją w pliku źródłowym. W przypadku nietradycyjnych języków pozycja dokumentu może być reprezentowana w inny sposób. Zobacz również *kontekst dokumentu*.

 błąd punktu przerwania w przypadku opisywania błędu w oczekującym punkcie przerwania. Punkt przerwania błędu może opisać błąd w lokalizacji oczekującego punktu przerwania, wyrażenie skojarzone z oczekującym punktem przerwania lub inne informacje, które uniemożliwiają oczekujący punkt przerwania z wiązania do lokalizacji kodu.

 kontekst oceny zapewnia abstrakcję kontekstu programowania na potrzeby oceny wyrażenia. Zazwyczaj kontekst oceny jest zakresem. Podczas obliczania wyrażenia w kontekście wyrażenia, kontekst wyrażenia zawiera reguły zakresu, które pasują do punktu tworzenia. Na przykład kontekst wyrażenia utworzony w ramce stosu zapewni kontekst do oceny zmiennych lokalnych, parametrów metody, elementów członkowskich klasy (jeśli dotyczy) i zmiennych globalnych.

 przechwycony wyjątek wyjątek, który jest przechwytywany przez aparat debugowania, nawet jeśli żaden mechanizm obsługi wyjątków nie znajduje się w bieżącej klatce stosu.

 JustMyCode koncepcję debugowania tylko kodu, który należy do użytkownika i ignoruje cały kod pośredni, taki jak kod systemowy — nawet jeśli kod źródłowy jest dostępny dla tego kodu systemowego.

 oczekujący punkt przerwania udostępnia streszczenie dla punktów przerwania przed, podczas i po załadowaniu kodu oraz sposób wirtualizacji punktów przerwania. Oczekujący punkt przerwania:

- Zawiera wszystkie informacje, które są konieczne do powiązania punktu przerwania z kodem w jednym lub większej liczbie programów.

- Może wiązać się z wieloma lokalizacjami w jednym lub kilku programach.

- Nigdy nie wiąże się z kodem.

  Za każdym razem, gdy jest ładowany kod, wszystkie oczekujące punkty przerwania w programie są sprawdzane w celu sprawdzenia, czy można utworzyć powiązanie. Oczekujący punkt przerwania jest określany jako zawierający wszystkie powiązane punkty przerwania, które tworzy.

  Przetwórz fizyczny proces Win32. Proces może zawierać wiele programów. Zobacz też *program*.

  programuje pojedynczą przestrzeń nazw działającą w ramach określonej architektury czasu wykonywania. Zobacz również *proces*.

  Menedżer debugowania sesji (SDM) zarządza dowolną liczbą aparatów debugowania, które debugują dowolną liczbę programów w wielu procesach na dowolnej liczbie komputerów. Na poziomie podstawowym model SDM jest multiplekserem aparatów debugowania. Ponadto model SDM zapewnia ujednolicony widok sesji debugowania do IDE.

  Ramka stosu reprezentuje stan obliczeń dla określonej ramki i szczególny poziom zagnieżdżonych wywołań funkcji.

  wątkowo uogólnione koncepcje wykonywania instrukcji opartych na stosie działające w co najmniej jednym programie.

  ostrzegawczy punkt przerwania dla opisywania ostrzeżenia w oczekującym punkcie przerwania. Punkt przerwania ostrzegawczy opisuje powód, dla którego oczekujący punkt przerwania nie został jeszcze powiązany z lokalizacją w kodzie. Może to być spowodowane tym, że kod nie został jeszcze załadowany do lokalizacji opisanej przez oczekujący punkt przerwania lub z innego powodu.

## <a name="see-also"></a>Zobacz też
- [Rozszerzalność debugera programu Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)

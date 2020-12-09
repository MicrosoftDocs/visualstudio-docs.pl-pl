---
title: Inspekcja wyjątku
titleSuffix: ''
description: Dowiedz się więcej na temat informacji dostępnych w programie Visual Studio, które ułatwiają debugowanie wyjątków i jak wybiórczo wyłączać wyjątki.
ms.custom: SEO-VS-2020
ms.date: 1/18/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- exception helper, debugger, exception
- debugging [Visual Studio], exception helper, Examine an exception
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ddc57d28510fe2e2cd5dbbb3aeea993813546715
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862818"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>Inspekcja wyjątku przy użyciu pomocnika wyjątków 

Postępowanie z wyjątkami jest typowym problemem, niezależnie od technologii lub poziomu wiedzy fachowej. Może to być frustrujące środowisko, które określa, dlaczego wyjątki powodują problemy w kodzie. Gdy debugujesz wyjątek w programie Visual Studio, chcemy zmniejszyć to frustrację, dostarczając odpowiednie informacje o wyjątku, aby ułatwić debugowanie problemu.

![Pomocnik wyjątków](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>Wstrzymaj przy wyjątku
Gdy debuger przerwie się na wyjątku, pojawia się ikona błędu wyjątku po prawej stronie tego wiersza kodu. Pomocnik wyjątku, który nie jest modalny, pojawi się obok ikony wyjątku.

![Pomocnik wyjątków obok wiersza kodu](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>Inspekcja informacji o wyjątku
Można natychmiast odczytać typ wyjątku i komunikat wyjątku w Pomocniku wyjątków oraz czy wyjątek został zgłoszony lub nieobsługiwany. Aby sprawdzić i wyświetlić właściwości obiektu wyjątku, kliknij link **Wyświetl szczegóły** .

## <a name="analyze-null-references"></a>Analizuj odwołania o wartości null
Począwszy od programu Visual Studio 2017, dla kodu .NET i C/C++, gdy trafisz `NullReferenceException` lub do `AccessViolation` , zobaczysz informacje o zerowej analizie w Pomocniku wyjątków. Analiza jest wyświetlana jako tekst poniżej komunikatu o wyjątku. Na poniższej ilustracji informacje są wyświetlane jako "**s** były puste".

![Analiza wartości null pomocnika wyjątków](media/debugger-exception-helper-default.png)


> [!NOTE]
> Analiza odwołań o wartości null w kodzie zarządzanym wymaga platformy .NET w wersji 4.6.2. Analiza wartości null nie jest obecnie obsługiwana w przypadku platforma uniwersalna systemu Windows (platformy UWP) i innych aplikacji platformy .NET Core. Jest on dostępny tylko podczas debugowania kodu, który nie ma żadnych optymalizacji kodu just-in-Time (JIT).

## <a name="configure-exception-settings"></a>Konfigurowanie ustawień wyjątków 
Można skonfigurować debuger, aby przerwać, gdy zostanie zgłoszony wyjątek bieżącego typu z sekcji **Ustawienia wyjątku** pomocnika wyjątków. Jeśli debuger jest wstrzymany w przypadku zgłoszonego wyjątku, można użyć pola wyboru, aby wyłączyć podział na ten typ wyjątku, gdy zostanie zgłoszony w przyszłości. Jeśli nie chcesz przerwać tego konkretnego wyjątku w przypadku zgłoszenia w tym konkretnym module, zaznacz pole wyboru według nazwy modułu w obszarze **except, gdy zostanie zgłoszony z:** w oknie **Ustawienia wyjątku** . 

## <a name="inspect-inner-exceptions"></a>Inspekcja wyjątków wewnętrznych 
Jeśli wyjątek ma wyjątki wewnętrzne ([InnerException](/dotnet/api/system.exception.innerexception), można je wyświetlić w Pomocniku wyjątków. Jeśli istnieje wiele wyjątków, można przechodzić między nimi za pomocą strzałek w lewo i w prawo widocznych powyżej stosu wywołań.

![Pomocnik wyjątków z wyjątkiem wewnętrznym](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>Inspekcja ponownie zgłoszonych wyjątków
W przypadkach, gdy wyjątek był `thrown` pomocnika wyjątków wyświetla stos wywołań od pierwszego uruchomienia wyjątku. Jeśli wyjątek został zgłoszony wiele razy, zostanie wyświetlony tylko stos wywołań z oryginalnego wyjątku.

![Pomocnik wyjątków z ponownie zgłoszonymi wyjątkami](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Udostępnianie sesji debugowania za pomocą Live Share
Z pomocnika wyjątków można uruchomić sesję [Live Share](/visualstudio/liveshare/) przy użyciu linku **Rozpocznij Live Share sesji..**.. Każda osoba łącząca się z sesją Live Share może zobaczyć pomocnika wyjątków wraz z innymi informacjami o debugowaniu.
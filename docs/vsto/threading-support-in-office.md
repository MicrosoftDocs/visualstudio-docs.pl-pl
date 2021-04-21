---
title: Obsługa wątkowych w pątków w psłudze Office
description: Wątkowanie jest obsługiwane w modelu Microsoft Office obiektów. Model obiektów pakietu Office nie jest bezpieczny wątkami, ale może współpracować z wieloma wątkami w rozwiązaniu pakietu Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dce8bb0667cecbe073c734595d341f9c7b7ccac9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826086"
---
# <a name="threading-support-in-office"></a>Obsługa wątkowych w pątków w psłudze Office
  Ten artykuł zawiera informacje na temat sposobu, w jaki wątkowanie jest obsługiwane Microsoft Office modelu obiektów. Model obiektów pakietu Office nie jest bezpieczny wątkami, ale można pracować z wieloma wątkami w rozwiązaniu pakietu Office. Aplikacje pakietu Office Component Object Model (COM). Com umożliwia klientom wywołanie serwerów COM na dowolnych wątkach. W przypadku serwerów COM, które nie są bezpieczne wątkowo, COM zapewnia mechanizm serializacji współbieżnych wywołań tak, aby w dowolnym momencie na serwerze był wykonywany tylko jeden wątek logiczny. Ten mechanizm jest nazywany modelem jednowątkowego typu "typu". Ponieważ wywołania są serializowane, wywołujące mogą być blokowane na okresy czasu, gdy serwer jest zajęty lub jest obsługa innych wywołań w wątku w tle.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>Wymagana wiedza w przypadku korzystania z wielu wątków
 Aby pracować z wieloma wątkami, musisz mieć co najmniej podstawową wiedzę na temat następujących aspektów wielowątkowania:

- Interfejsy API systemu Windows

- Pojęcia wielowątkowe COM

- Współbieżność

- Synchronizacja

- Marshaling

  Aby uzyskać ogólne informacje na temat wielowątkowania, zobacz [Managed threading (Zarządzana wątkowa).](/dotnet/standard/threading/)

  Pakiet Office działa w głównym urzędzie stacyjki. Zrozumienie implikacji tej funkcji umożliwia zrozumienie sposobu używania wielu wątków z pakietem Office.

## <a name="basic-multithreading-scenario"></a>Podstawowy scenariusz wielowątkowych
 Kod w rozwiązaniach pakietu Office zawsze jest uruchamiany w głównym wątku interfejsu użytkownika. Wydajność aplikacji można wygładzić, uruchamiając oddzielne zadanie w wątku w tle. Celem jest wykonanie dwóch zadań pozornie jednocześnie zamiast jednego zadania, po którym następuje drugie, co powinno skutkować płynniejszym wykonywaniem (głównym powodem używania wielu wątków). Na przykład możesz mieć kod zdarzenia w głównym wątku interfejsu użytkownika programu Excel, a w wątku w tle możesz uruchomić zadanie, które zbiera dane z serwera i aktualizuje komórki w interfejsie użytkownika programu Excel przy użyciu danych z serwera.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Wątki w tle, które wywołują model obiektów pakietu Office
 Gdy wątek w tle wykonuje wywołanie do aplikacji pakietu Office, wywołanie jest automatycznie marshaledowane przez granicę stajni. Nie ma jednak gwarancji, że aplikacja pakietu Office może obsłużyć wywołanie w momencie jego wywołania w wątku w tle. Istnieje kilka możliwości:

1. Aplikacja pakietu Office musi wysyłać komunikaty, aby wywołanie było w stanie wprowadzić komunikat. W przypadku intensywnego przetwarzania bez jego wywnioskowania może to zająć trochę czasu.

2. Jeśli w woluminie znajduje się już inny wątek logiczny, nie można wprowadzić nowego wątku. Dzieje się tak często, gdy wątek logiczny wchodzi do aplikacji pakietu Office, a następnie wykonuje ponowne wywołanie do języka wywołującego. Aplikacja jest blokowana w oczekiwaniu na powrót tego wywołania.

3. Program Excel może być w stanie, w którym nie może natychmiast obsłużyć wywołania przychodzącego. Na przykład aplikacja pakietu Office może wyświetlać modalne okno dialogowe.

   W przypadku możliwości 2 i 3 com udostępnia [interfejs IMessageFilter.](/windows/desktop/api/objidl/nn-objidl-imessagefilter) Jeśli serwer go implementuje, wszystkie wywołania są wprowadzane za pośrednictwem [metody HandleIncomingCall.](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) W przypadku możliwości 2 wywołania są automatycznie odrzucane. W przypadku możliwości 3 serwer może odrzucić wywołanie, w zależności od okoliczności. Jeśli wywołanie zostanie odrzucone, wywołujący musi zdecydować, co zrobić. Zwykle wywołujący implementuje metodę [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), w takim przypadku zostanie powiadomiony o odrzuceniu przez metodę [RetryRejectedCall.](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall)

   Jednak w przypadku rozwiązań utworzonych przy użyciu narzędzi programistyczych pakietu Office w usłudze Visual Studio międzyoptymator com konwertuje wszystkie odrzucone wywołania na ("Filtr komunikatów wskazuje, że aplikacja jest <xref:System.Runtime.InteropServices.COMException> zajęta"). Za każdym razem, gdy model obiektu jest wywołany w wątku w tle, należy przygotować się do obsługi tego wyjątku. Zwykle obejmuje to ponawianie próby przez pewien czas, a następnie wyświetlanie okna dialogowego. Można jednak również utworzyć wątek w tle jako STA, a następnie zarejestrować filtr komunikatów dla tego wątku, aby obsłużyć ten przypadek.

## <a name="start-the-thread-correctly"></a>Poprawne uruchamianie wątku
 Podczas tworzenia nowego wątku STA należy ustawić stan chłoniaka na STA przed uruchomieniem wątku. Poniższy przykład kodu pokazuje, jak to zrobić.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs" id="Snippet5":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb" id="Snippet5":::

 Aby uzyskać więcej informacji, zobacz [Najlepsze rozwiązania dotyczące wątków zarządzanych.](/dotnet/standard/threading/managed-threading-best-practices)

## <a name="modeless-forms"></a>Formularze nie modeless
 Formularz nie moderowania umożliwia pewien typ interakcji z aplikacją podczas wyświetlania formularza. Użytkownik wchodzi w interakcję z formularzem, a formularz wchodzi w interakcję z aplikacją bez zamykania. Model obiektów pakietu Office obsługuje formularze zarządzane bez trybów. Nie należy ich jednak używać w wątku w tle.

## <a name="see-also"></a>Zobacz też
- [Wątkowanie (C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [Wątkowanie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [Używanie wątków i wątkowych](/dotnet/standard/threading/using-threads-and-threading)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)

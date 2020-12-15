---
title: Obsługa wątkowości w pakiecie Office
description: Obsługa wątków jest obsługiwana w modelu obiektów Microsoft Office. Model obiektów pakietu Office nie jest bezpieczny dla wątków, ale może współdziałać z wieloma wątkami w rozwiązaniu pakietu Office.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5d44c86e17b5df79c44f85cd555b3036e925ae61
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524190"
---
# <a name="threading-support-in-office"></a>Obsługa wątkowości w pakiecie Office
  Ten artykuł zawiera informacje dotyczące sposobu obsługi wątków w modelu obiektów Microsoft Office. Model obiektów pakietu Office nie jest bezpieczny wątkowo, ale możliwe jest współdziałanie z wieloma wątkami w rozwiązaniu pakietu Office. Aplikacje pakietu Office to serwery Component Object Model (COM). COM umożliwia klientom wywoływanie serwerów COM w dowolnych wątkach. W przypadku serwerów COM, które nie są bezpieczne wątkowo, COM udostępnia mechanizm serializowania współbieżnych wywołań, tak aby tylko jeden wątek logiczny był wykonywany na serwerze w dowolnym momencie. Ten mechanizm jest znany jako model jednowątkowego apartamentu (STA). Ponieważ wywołania są serializowane, obiekty wywołujące mogą być blokowane przez okres czasu, gdy serwer jest zajęty lub obsługuje inne wywołania w wątku w tle.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>Wiedza jest wymagana w przypadku korzystania z wielu wątków
 Aby współpracować z wieloma wątkami, musisz mieć co najmniej podstawową wiedzę na temat następujących aspektów wielowątkowości:

- Interfejsy API systemu Windows

- Koncepcje wielowątkowości COM

- Współbieżność

- Synchronizacja

- Marshaling

  Aby uzyskać ogólne informacje na temat wielowątkowości, zobacz [zarządzane wątki](/dotnet/standard/threading/).

  Pakiet Office działa w głównym STA. Zrozumienie konsekwencji tego sprawia, że można zrozumieć, jak używać wielu wątków z pakietem Office.

## <a name="basic-multithreading-scenario"></a>Podstawowy scenariusz wielowątkowości
 Kod w rozwiązaniach pakietu Office jest zawsze uruchamiany w głównym wątku interfejsu użytkownika. Możesz chcieć wygładzić wydajność aplikacji, uruchamiając oddzielne zadanie w wątku w tle. Celem jest wykonanie dwóch zadań jednocześnie, zamiast jednego zadania, po którym następuje inne działanie, które powinno spowodować wygładzenie wykonania (główny powód użycia wielu wątków). Na przykład kod zdarzenia może znajdować się w głównym wątku interfejsu użytkownika programu Excel i w wątku w tle można uruchomić zadanie, które zbiera dane z serwera i aktualizuje komórki w interfejsie użytkownika programu Excel danymi z serwera.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Wątki w tle, które odwołują się do modelu obiektów pakietu Office
 Gdy wątek w tle wykonuje wywołanie do aplikacji pakietu Office, wywołanie jest automatycznie organizowane na granicy STA. Nie ma jednak gwarancji, że aplikacja pakietu Office może obsłużyć wywołanie w momencie, gdy wątek w tle go tworzy. Istnieje kilka możliwości:

1. Aplikacja pakietu Office musi wypompować komunikaty, aby można było wprowadzić tę możliwość. W przypadku intensywnego przetwarzania bez podania tego czasu może to potrwać.

2. Jeśli inny wątek logiczny jest już w Apartament, nie można wprowadzić nowego wątku. Zdarza się to często, gdy wątek logiczny wchodzi do aplikacji pakietu Office, a następnie wykonuje wywołanie zwrotne do apartamentu obiektu wywołującego. Aplikacja jest blokowana, ponieważ oczekuje na zwrócenie tego wywołania.

3. Program Excel może być w stanie, w którym nie może natychmiast obsłużyć połączenia przychodzącego. Na przykład aplikacja pakietu Office może wyświetlać modalne okno dialogowe.

   W przypadku możliwości 2 i 3 model COM udostępnia interfejs [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) . Jeśli serwer implementuje ten proces, wszystkie wywołania są wprowadzane przez metodę [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) . W przypadku możliwości 2 wywołania są automatycznie odrzucane. W przypadku możliwości 3 serwer może odrzucić wywołanie, w zależności od okoliczności. Jeśli wywołanie zostanie odrzucone, obiekt wywołujący musi zdecydować, co należy zrobić. Zwykle obiekt wywołujący implementuje [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter), w takim przypadku można powiadomić o odrzuceniu przez metodę [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) .

   Jednak w przypadku rozwiązań utworzonych przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, program COM Interop konwertuje wszystkie odrzucone wywołania na <xref:System.Runtime.InteropServices.COMException> ("Filtr komunikatów wskazuje, że aplikacja jest zajęta"). Za każdym razem, gdy nastąpi wywołanie modelu obiektu w wątku w tle, należy przygotować się do obsługi tego wyjątku. Zwykle, która obejmuje ponawianie próby przez określony czas, a następnie wyświetlenie okna dialogowego. Można jednak również utworzyć wątek w tle jako STA, a następnie zarejestrować filtr komunikatów dla tego wątku w celu obsługi tego przypadku.

## <a name="start-the-thread-correctly"></a>Uruchom wątek prawidłowo
 Podczas tworzenia nowego wątku STA Ustaw stan Apartment na STA przed rozpoczęciem wątku. Poniższy przykład kodu demonstruje, jak to zrobić.

 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]

 Aby uzyskać więcej informacji, zobacz temat [zarządzane wątki z najlepszymi rozwiązaniami](/dotnet/standard/threading/managed-threading-best-practices).

## <a name="modeless-forms"></a>Formularze niemodalne
 Formularz niemodalny umożliwia pewien typ interakcji z aplikacją podczas wyświetlania formularza. Użytkownik współdziała z formularzem, a formularz współdziała z aplikacją bez zamykania. Model obiektów pakietu Office obsługuje zarządzane formularze niemodalne; nie należy jednak używać ich w wątku w tle.

## <a name="see-also"></a>Zobacz też
- [Wątkowość (C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [Wątkowość (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [Używanie wątków i wątkowości](/dotnet/standard/threading/using-threads-and-threading)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)

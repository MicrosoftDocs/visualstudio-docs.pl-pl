---
title: Nie można ustawić punktu przerwania danych | Microsoft Docs
description: Znajdź wyjaśnienia, rozwiązania i obejścia dla błędu "Nie można ustawić błędów punktu przerwania danych", które występują podczas używania funkcji "Przerwij, gdy wartość zmienia się".
ms.custom: SEO-VS-2020
ms.date: 5/19/2020
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unable_to_set_data_breakpoint
dev_langs:
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, data breakpoint
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: wardengnaw
ms.author: waan
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 73e7e02d90e2a89c81b5e690718c95fe7efe0fb3
ms.sourcegitcommit: 6e27b1238a8aa704b127eac34f4173e9d56690c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2021
ms.locfileid: "110231968"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Rozwiązywanie problemów z błędami punktu przerwania danych
Ta strona zawiera informacje na temat rozwiązywania typowych błędów występujących podczas używania funkcji "Przerwij, gdy wartość zmienia się"

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>Diagnozowanie błędów "Nie można ustawić punktu przerwania danych"
> [!IMPORTANT]
> Zarządzane punkty przerwania danych są obsługiwane w programie .NET Core 3.0 i jego up oraz w programie .NET 5.0.3 i jego up. Najnowszą wersję można pobrać [tutaj.](https://dotnet.microsoft.com/download)

Poniżej znajduje się lista błędów, które mogą wystąpić podczas korzystania z zarządzanych punktów przerwania danych. Zawierają one więcej informacji na temat przyczyny błędu oraz możliwych rozwiązań lub obejść w celu usunięcia błędu.

- *"Wersja programu .NET używana przez proces docelowy nie obsługuje punktów przerwania danych. Punkty przerwania danych wymagają programu .NET Core 3.x lub .NET 5.0.3+, działającego w wersji x86 lub x64".*

  - Obsługa zarządzanych punktów przerwania danych rozpoczęła się na platformie .NET Core 3.0. Nie jest ona obecnie obsługiwana w .NET Framework, wersjach programu .NET Core w wersji 3.0 ani wersjach programu .NET w wersji 5.0.3. 
    
  - **Rozwiązanie:** Rozwiązaniem tego problemu jest uaktualnienie projektu do programu .NET Core 3.0.

- *"Nie można znaleźć wartości na zarządzanym stosie i nie można jej śledzić".*
  - Zmienna zadeklarowana na stosie.
    - Nie obsługujemy ustawiania punktów przerwania danych dla zmiennych utworzonych na stosie, ponieważ ta zmienna będzie nieprawidłowa po zakończeniu działania funkcji.
    - **Obejście:** Ustaw punkty przerwania w wierszach, w których jest używana zmienna.

  - "Przerwij, gdy wartość zmienia się" dla zmiennej, która nie jest rozwijana z listy rozwijanej.
    - Debuger wewnętrznie musi znać obiekt zawierający pole, które chcesz śledzić. Moduł odśmiecania pamięci może poruszać obiekt w stercie, więc debuger musi znać obiekt, który zawiera zmienną, którą chcesz śledzić. 
    - **Obejście:** Jeśli znajdujesz się w metodzie w obiekcie, dla którego chcesz ustawić punkt przerwania danych, przejdź w górę o jedną ramkę i użyj okna, aby rozwinąć obiekt i ustawić punkt przerwania danych dla `locals/autos/watch` odpowiedniego pola.

- *"Punkty przerwania danych nie są obsługiwane w przypadku pól statycznych ani właściwości statycznych".*
    
  - Pola statyczne i właściwości nie są obecnie obsługiwane. Jeśli interesuje Cię ta funkcja, prosimy o [opinię.](#provide-feedback)

- *"Nie można śledzić pól i właściwości struktur".*

  - Pola i właściwości struktur nie są obecnie obsługiwane. Jeśli interesuje Cię ta funkcja, prosimy o [opinię.](#provide-feedback)

- *"Wartość właściwości została zmieniona i nie można już jej śledzić".*

  - Właściwość może zmienić sposób jej obliczania w czasie wykonywania. Jeśli tak się stanie, liczba zmiennych, od których zależy właściwość, zwiększa się i może przekraczać ograniczenie sprzętowe. Zobacz `"The property is dependent on more memory than can be tracked by the hardware."` poniżej.

- *"Właściwość jest zależna od większej ilości pamięci niż może być śledzona przez sprzęt".*
    
  - Każda architektura ma ustawioną liczbę bajtów i punktów przerwania danych sprzętowych, które może obsługiwać, a właściwość, dla których chcesz ustawić punkt przerwania danych, przekroczyła ten limit. Zapoznaj się z tabelą [Ograniczenia](#data-breakpoint-hardware-limitations) sprzętowe punktu przerwania danych, aby dowiedzieć się, ile punktów przerwania danych obsługiwanych przez sprzęt i bajtów jest dostępnych dla architektury, z których korzystasz. 
  - **Obejście:** Ustaw punkt przerwania danych na wartość, która może ulec zmianie we właściwości .

- *"Punkty przerwania danych nie są obsługiwane w przypadku korzystania ze starszej wersji ewaluatora wyrażeń języka C#".*

  - Punkty przerwania danych są obsługiwane tylko w przypadku programu ewaluatora wyrażeń języka C# w wersji starszej niż starsza. 
  - **Rozwiązanie:** wyłączysz starszą ewaluator wyrażeń języka C#, przechodząc do pola `Debug -> Options` wyboru `Debugging -> General` `"Use the legacy C# and VB expression evaluators"` .

- *"Klasa **X** ma niestandardowy widok debugera, który blokuje używanie punktów przerwania danych w danych specyficznych tylko dla niego".*
  
  - Punkty przerwania danych są obsługiwane tylko w pamięci utworzonej przez proces docelowy (debugowana aplikacja). Pamięć, w której ustawiany jest punkt przerwania danych, została oflagowana jako prawdopodobnie należąca do obiektu utworzonego przez atrybut [DebuggerTypeProxy](using-debuggertypeproxy-attribute.md) lub coś innego, co nie jest częścią procesu docelowego.
  - **Obejście:** Rozwiń "Nieprzetworzny widok" obiektów zamiast rozwijać widok DebuggerTypeProxy obiektów, a następnie ustaw punkt przerwania danych. Gwarantuje to, że punkt przerwania danych nie znajduje się w pamięci należącej do obiektu utworzonego przez atrybut DebuggerTypeProxy.

## <a name="data-breakpoint-hardware-limitations"></a>Ograniczenia sprzętowe punktu przerwania danych

Architektura (konfiguracja platformy), na której działa program, ma ograniczoną liczbę punktów przerwania danych sprzętowych, których może używać. W poniższej tabeli przedstawiono, ile rejestrów jest dostępnych do użycia na architekturę.

| Architektura | Liczba punktów przerwania danych obsługiwanych przez sprzęt | Maksymalny rozmiar bajtów|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Wyraź opinię

W przypadku jakichkolwiek problemów lub sugestii dotyczących tej funkcji skontaktuj się z nami za pośrednictwem usługi Help > Send Feedback > [Report a Problem](../ide/how-to-report-a-problem-with-visual-studio.md) in the IDE or in the [Developer Community](https://aka.ms/feedback/suggest?space=8)(Zgłoś problem w programie IDE lub w Developer Community).

## <a name="see-also"></a>Zobacz też

- [Używanie funkcji "Przerwij, gdy wartość zmienia się" w programie .NET Core 3.0.](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)
- [DevBlog: Break When Value Changes: Data Breakpoints for .NET Core in Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)

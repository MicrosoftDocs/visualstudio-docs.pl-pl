---
title: Błąd — nie można ustawić punktu przerwania danych | Microsoft Docs
ms.date: 12/3/2019
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
ms.openlocfilehash: 20e3ea1cb0124e6bdfb93e023021673ca2e34602
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88248744"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Rozwiązywanie problemów z błędami punktów przerwania danych
Ta strona zawiera instrukcje dotyczące rozwiązywania typowych błędów, które pojawiają się podczas korzystania z funkcji "Przerwij przy zmianie wartości".

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>Diagnozowanie błędów "nie można ustawić punktu przerwania danych"
> [!IMPORTANT]
> Zarządzane punkty przerwania danych są obsługiwane w programie .NET Core 3,0 i w górę. Najnowszą wersję możesz pobrać [tutaj](https://dotnet.microsoft.com/download).

Poniżej znajduje się lista błędów, które mogą wystąpić podczas korzystania z punktów przerwania zarządzanych danych. Zawierają one dodatkowe wyjaśnienie przyczyny wystąpienia błędu oraz możliwe rozwiązania lub obejścia problemu.

- *"Wersja platformy .NET używana przez proces docelowy nie obsługuje punktów przerwania danych. Punkty przerwania danych wymagają programu .NET Core 3.0 + uruchomionego na x86 lub x64 ".*

  - Obsługa punktów przerwania zarządzanych danych rozpoczęła się w programie .NET Core 3,0. Nie jest to obecnie obsługiwane w .NET Framework lub wersji programu .NET Core w systemie 3,0. 
    
  - **Rozwiązanie**: rozwiązanie to może spowodować uaktualnienie projektu do programu .net Core 3,0.

- *"Nie można odnaleźć wartości na stercie zarządzanym i nie można jej śledzić".*
  - Zmienna zadeklarowana na stosie.
    - Nie obsługujemy ustawiania punktów przerwania danych dla zmiennych utworzonych na stosie, ponieważ ta zmienna będzie nieprawidłowa po zamknięciu funkcji.
    - **Obejście**: Ustaw punkty przerwania w wierszach, w których jest używana zmienna.

  - "Przerwij, gdy zmienia się wartość" w zmiennej, która nie jest rozwinięta z listy rozwijanej.
    - Debuger wewnętrznie musi znać obiekt zawierający pole, które ma być śledzone. Moduł wyrzucania elementów bezużytecznych może przenieść obiekt wokół sterty, aby debuger musiał znać obiekt, który utrzymuje zmienną, którą chcesz śledzić. 
    - **Obejście**: Jeśli korzystasz z metody w obiekcie, dla którego chcesz ustawić punkt przerwania danych, przejdź do jednej ramki i Użyj `locals/autos/watch` okna do rozwinięcia obiektu i ustaw punkt przerwania danych w polu, które chcesz.

- *"Punkty przerwania danych nie są obsługiwane w przypadku pól statycznych lub właściwości statycznych".*
    
  - Pola i właściwości statyczne nie są obecnie obsługiwane. Jeśli interesuje Cię tę funkcję, Przekaż [opinię](#provide-feedback).

- *"Pola i właściwości struktur nie mogą być śledzone".*

  - Pola i właściwości struktur nie są obecnie obsługiwane. Jeśli interesuje Cię tę funkcję, Przekaż [opinię](#provide-feedback).

- *"Wartość właściwości została zmieniona i nie może już być śledzona".*

  - Właściwość może zmienić sposób, w jaki jest obliczany w czasie wykonywania, a jeśli tak się stanie, liczba zmiennych, które zależy od wzrostu i może przekroczyć ograniczenie sprzętowe. Zobacz `"The property is dependent on more memory than can be tracked by the hardware."` poniżej.

- *"Właściwość jest zależna od większej ilości pamięci, niż może być śledzona przez sprzęt".*
    
  - Każda architektura ma ustawioną liczbę bajtów i punkty przerwania danych sprzętowych, które może obsłużyć i właściwość, dla której ma zostać ustawiony punkt przerwania danych, przekroczyła ten limit. Zapoznaj się z tabelą [ograniczeń sprzętowych punktów przerwania danych](#data-breakpoint-hardware-limitations) , aby dowiedzieć się, ile zasobów punktów przerwania i bajtów danych jest dostępnych dla używanej architektury. 
  - **Obejście**: Ustaw punkt przerwania danych dla wartości, która może ulec zmianie we właściwości.

- *"Punkty przerwania danych nie są obsługiwane w przypadku używania starszej ewaluatora wyrażeń języka C#".*

  - Punkty przerwania danych są obsługiwane tylko na niestarszej ewaluatora wyrażeń języka C#. 
  - **Rozwiązanie**: nie można wyłączyć starszej kolekcji wyrażeń języka C#, przechodząc do pozycji `Debug -> Options` `Debugging -> General` Usuń zaznaczenie `"Use the legacy C# and VB expression evaluators"` .

## <a name="data-breakpoint-hardware-limitations"></a>Ograniczenia sprzętowe danych punktów przerwania

Architektura (Konfiguracja platformy), w której działa program, zawiera ograniczoną liczbę punktów przerwania danych sprzętowych, których można użyć. Poniższa tabela wskazuje, ile rejestrów jest dostępnych do użycia na architekturę.

| Architektura | Liczba obsługiwanych przez sprzęt punktów przerwania danych | Maksymalny rozmiar bajtu|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Wyraź opinię

Aby dowiedzieć się więcej na temat problemów lub sugestii dotyczących tej funkcji, skontaktuj się z pomocą techniczną, aby uzyskać pomoc w > wysłania opinii > [zgłosić problem](../ide/how-to-report-a-problem-with-visual-studio.md) w środowisku IDE lub [społeczności deweloperów](https://developercommunity.visualstudio.com/).

## <a name="see-also"></a>Zobacz też

- [Używanie funkcji "Przerwij, gdy zmiany wartości" w programie .NET Core 3,0](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).
- [DevBlog: Przerwij w przypadku zmiany wartości: punkty przerwania danych dla platformy .NET Core w programie Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)

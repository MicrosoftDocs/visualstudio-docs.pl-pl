---
title: Obsługiwane zmiany kodu (C# i Visual Basic) | Dokumentacja firmy Microsoft
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 865b5c220a410c9b0d744263820a50dd1bb9395a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878630"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Obsługiwane zmiany kodu (C# i Visual Basic)
Edytuj i Kontynuuj obsługuje większość typów zmian kodu w treści metod. Większość zmian poza treści metod i drobne zmiany w treści metod, nie można zastosować podczas debugowania, jednak. Aby zastosować te nieobsługiwane zmiany, należy zatrzymać debugowanie i ponownie uruchom za pomocą nowej wersji kodu.

## <a name="supported-changes-to-code"></a>Obsługiwane zmiany kodu

W poniższej tabeli przedstawiono zmiany wprowadzone do C# i kodu języka Visual Basic podczas sesji debugowania, bez konieczności ponownego uruchamiania sesji.

|Funkcji element języka|Operacja edytowania obsługiwane|Ograniczenia|
|-|-|-|
|Types|Dodaj metody, pola, konstruktory, et al|[Tak](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iteratory|Dodawanie lub modyfikowanie|Nie|
|Async/await wyrażeń|Dodawanie lub modyfikowanie|[Tak](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Obiekty dynamiczne|Dodawanie lub modyfikowanie|Nie|
|wyrażenia lambda|Dodawanie lub modyfikowanie|[Tak](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Wyrażenia LINQ|Dodawanie lub modyfikowanie|[Takie same jak wyrażenia lambda](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Nowszych funkcji języka, takich jak Interpolacja ciągów i operatorów warunkowych działających z wartością null są zazwyczaj obsługiwane przez Edytuj i Kontynuuj. Aby uzyskać najnowsze informacje, zobacz [Enc obsługiwane edycje](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) strony.

## <a name="unsupported-changes-to-code"></a>Nieobsługiwane zmiany do kodu
 Nie można zastosować następujące zmiany do C# i kodu języka Visual Basic podczas sesji debugowania:  
  
-   Zmiany bieżącej instrukcji lub aktywnej instrukcji.  
  
     Aktywne instrukcje obejmują dowolnej instrukcji w funkcjach w stosie wywołań, które zostały wywołane do bieżącej instrukcji.  
  
     Bieżąca instrukcja jest oznaczony za żółtym tłem w oknie źródła. Inne aktywne instrukcje są oznaczane przez cieniowanego tła i są przeznaczone tylko do odczytu. Te kolory domyślne można zmienić w programie **opcje** okno dialogowe.

- W poniższej tabeli przedstawiono nieobsługiwanych zmian kodu przez element języka.

|Funkcji element języka|Operacja nieobsługiwana edytowania|
|-|-|
|Wszystkie elementy kodu|Zmiana nazwy|
|Namespaces|Dodaj|
|Przestrzenie nazw, typy, elementy członkowskie|Usuwanie|
|Typy ogólne|Dodawanie lub modyfikowanie|
|Interfejsy|Modyfikowanie|
|Types|Dodawanie elementu członkowskiego abstrakcyjne lub wirtualne, Dodaj zastąpienie (zobacz [szczegóły](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Types|Dodaj destruktor|
|Elementy członkowskie|Modyfikowanie członka, który odwołuje się do osadzonego typu międzyoperacyjnego|
|Elementy członkowskie (Visual Basic)|Zmodyfikuj element członkowski o instrukcja On Error lub Wznów|
|Elementy członkowskie (Visual Basic)|Modyfikowanie członka zawierający wartość zagregowaną, Group By, proste łączenie lub LINQ Dołącz do grupy klauzula zapytania|
|Metody|Modyfikowanie podpisów|
|Metody|Podejmuj metodę abstrakcyjną stają się nieabstrakcyjnej, dodanie treści metody|
|Metody|Usuń treść metody|
|Atrybuty|Dodawanie lub modyfikowanie|
|Właściwości lub zdarzenia|Zmodyfikuj parametr typu, typ podstawowy typ delegata lub typ zwracany |
|Operatory lub indeksatorów|Zmodyfikuj parametr typu, typ podstawowy typ delegata lub typ zwracany |
|bloki catch|Modyfikowanie, gdy zawiera on aktywnej instrukcji|
|bloki try-catch-finally|Modyfikowanie, gdy zawiera on aktywnej instrukcji|
|instrukcje using|Dodaj|
|lambdy metody asynchroniczne|Modyfikowanie lambdy asynchronicznej metody/w projektach przeznaczonych dla platformy .NET Framework 4 i zmniejszyć (zobacz [szczegóły](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iteratory|Modyfikowanie iterator w projektach przeznaczonych dla platformy .NET Framework 4 i zmniejszyć (zobacz [szczegóły](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
  
## <a name="unsafe-code"></a>Niebezpieczny kod  
 Zmiany w niebezpieczny kod mają te same ograniczenia co wprowadzenia zmian w kodzie bezpiecznym, za pomocą jednego dodatkowych ograniczeń: Edytuj i Kontynuuj nie obsługuje zmiany niebezpieczny kod, który istnieje w metodzie, która zawiera `stackalloc` operatora.  

## <a name="unsupported-app-scenarios"></a>Scenariusze nieobsługiwane aplikacji

Platform i nieobsługiwanych aplikacji obejmują platformy ASP.NET 5, Silverlight 5 i Windows 8.1.

> [!NOTE]
> Aplikacje, które są obsługiwane to platformy uniwersalnej systemu Windows w systemie Windows 10 i x86 i x64 aplikacji, przeznaczonych dla platformy .NET Framework 4.6 pulpitu lub nowszej wersji (.NET Framework jest tylko wersja desktop).
  
## <a name="unsupported-scenarios"></a>Nieobsługiwane scenariusze  
 Edytuj i Kontynuuj nie jest dostępna w następujących scenariuszach debugowania:  
  
-   Debugowanie trybu mieszanego (natywnego/zarządzanego).  
  
-   Debugowanie SQL.  
  
-   Debugowanie odzyskiwania po awarii. Zrzut programu Watson.  
  
-   Debugowanie aplikacji osadzonego środowiska uruchomieniowego.  
  
-   Debugowanie aplikacji przy użyciu dołączyć do procesu (**debugowania > Dołącz do procesu**) zamiast uruchamiania aplikacji, wybierając **Start** z **debugowania** menu.  
  
-   Debugowanie zoptymalizowanego kodu.  
  
-   Debugowanie starą wersję kodu po nowej wersji nie powiodło się skompilowanie z powodu błędów kompilacji.
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i Kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Instrukcje: Użyj funkcji Edytuj i Kontynuuj (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
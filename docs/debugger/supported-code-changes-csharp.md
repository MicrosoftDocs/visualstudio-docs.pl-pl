---
title: Obsługiwane zmiany kodu (C# i Visual Basic) | Microsoft Docs
ms.date: 10/11/2018
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c480fad064cad602ea3fd19153d53f0276815d30
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509422"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Obsługiwane zmiany kodu (C# i Visual Basic)
Edytuj i Kontynuuj obsługuje większość typów zmian kodu w treści metody. Większość zmian poza treściami metod oraz kilka zmian w obrębie treści metody nie można zastosować podczas debugowania. Aby zastosować te nieobsługiwane zmiany, należy zatrzymać debugowanie i ponownie uruchomić za pomocą nowej wersji kodu.

## <a name="supported-changes-to-code"></a>Obsługiwane zmiany w kodzie

W poniższej tabeli przedstawiono zmiany, które mogą zostać wprowadzone w języku C# i Visual Basic kodu podczas sesji debugowania bez ponownego uruchamiania sesji.

|Element/funkcja języka|Obsługiwana operacja edycji|Ograniczenia|
|-|-|-|
|Types|Dodawanie metod, pól, konstruktorów, et al|[Tak](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Iteratory|Dodaj lub zmodyfikuj|Nie|
|wyrażenia asynchroniczne/await|Dodaj lub zmodyfikuj|[Tak](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Obiekty dynamiczne|Dodaj lub zmodyfikuj|Nie|
|wyrażenia lambda|Dodaj lub zmodyfikuj|[Tak](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Wyrażenia LINQ|Dodaj lub zmodyfikuj|[Analogicznie jak wyrażenia lambda](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|

> [!NOTE]
> Nowsze funkcje języka, takie jak interpolacja ciągów i operatory warunkowe o wartości null, są ogólnie obsługiwane przez funkcję Edytuj i Kontynuuj. Najbardziej aktualne informacje można znaleźć na stronie [zmiany obsługiwane](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md) przez program Enc.

## <a name="unsupported-changes-to-code"></a>Nieobsługiwane zmiany w kodzie
 Następujące zmiany nie mogą zostać zastosowane do kodu C# i Visual Basic podczas sesji debugowania:

- Zmiany bieżącej instrukcji lub dowolnej innej aktywnej instrukcji.

     Aktywne instrukcje obejmują wszystkie instrukcje w funkcjach w stosie wywołań, które zostały wywołane w celu uzyskania bieżącej instrukcji.

     Bieżąca instrukcja jest oznaczona za pomocą żółtego tła w oknie źródło. Inne aktywne instrukcje są oznaczone cieniowanym tłem i są tylko do odczytu. Te domyślne kolory można zmienić w oknie dialogowym **Opcje** .

- W poniższej tabeli przedstawiono nieobsługiwane zmiany kodu przez element języka.

|Element/funkcja języka|Nieobsługiwana operacja edycji|
|-|-|
|Wszystkie elementy kodu|Zmiana nazwy|
|Namespaces|Dodaj|
|Przestrzenie nazw, typy, elementy członkowskie|Usuń|
|Typy ogólne|Dodaj lub zmodyfikuj|
|Interfejsy|Modyfikowanie|
|Types|Dodawanie abstrakcyjnej lub wirtualnej składowej, Dodawanie przesłonięcia (zobacz [szczegóły](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|
|Types|Dodaj destruktor|
|Elementy członkowskie|Modyfikowanie elementu członkowskiego odwołującego się do osadzonego typu międzyoperacyjnego|
|Elementy członkowskie|Modyfikowanie statycznego elementu członkowskiego, po którym został już uzyskany dostęp przez wykonanie kodu|
|Elementy członkowskie (Visual Basic)|Modyfikowanie elementu członkowskiego za pomocą instrukcji with Error lub Resume|
|Elementy członkowskie (Visual Basic)|Modyfikowanie elementu członkowskiego zawierającego klauzulę zapytania LINQ, Group by, Simple Join lub Group Join|
|Metody|Modyfikuj podpisy|
|Metody|Ustaw metodę abstrakcyjną jako nieabstrakcyjną przez dodanie treści metody|
|Metody|Usuń treść metody|
|Atrybuty|Dodaj lub zmodyfikuj|
|Zdarzenia lub właściwości|Modyfikowanie parametru typu, typu podstawowego, typu delegata lub typu zwracanego |
|Operatory lub indeksatory|Modyfikowanie parametru typu, typu podstawowego, typu delegata lub typu zwracanego |
|bloki catch|Modyfikuj, gdy zawiera aktywną instrukcję|
|bloki try-catch-finally|Modyfikuj, gdy zawiera aktywną instrukcję|
|instrukcje using|Dodaj|
|metody asynchroniczne/wyrażenia lambda|Modyfikuj metodę asynchroniczną/wyrażenie lambda w projekcie docelowym .NET Framework 4 i niższym (zobacz [szczegóły](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|
|Iteratory|Modyfikowanie iteratora w projekcie docelowym .NET Framework 4 i niższym (zobacz [szczegóły](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md))|

## <a name="unsafe-code"></a>Niebezpieczny kod
 Zmiany w niebezpiecznym kodzie mają takie same ograniczenia jak zmiany w bezpiecznym kodzie, z jednym dodatkowym ograniczeniem: polecenie Edytuj i Kontynuuj nie obsługuje zmian w niebezpiecznym kodzie, który opuszcza metodę, która zawiera `stackalloc` operator.

## <a name="unsupported-app-scenarios"></a>Nieobsługiwane scenariusze aplikacji

Nieobsługiwane aplikacje i platformy obejmują ASP.NET 5, Silverlight 5 i Windows 8.1.

> [!NOTE]
> Obsługiwane aplikacje obejmują platformy UWP w systemie Windows 10 oraz aplikacje x86 i x64 przeznaczone dla .NET Framework 4,6 Desktop lub nowszych (.NET Framework jest tylko wersja klasyczna).

## <a name="unsupported-scenarios"></a>Nieobsługiwane scenariusze
 Edytuj i Kontynuuj nie są dostępne w następujących scenariuszach debugowania:

- Debugowanie w trybie mieszanym (natywnym/zarządzanym).

- Debugowanie SQL.

- Debugowanie zrzutu Dr. Watson.

- Debugowanie osadzonej aplikacji środowiska uruchomieniowego.

- Debugowanie aplikacji przy użyciu funkcji dołączania do procesu (**debugowanie > dołączanie do procesu**) zamiast uruchamiania aplikacji, wybierając pozycję **Rozpocznij** z menu **Debuguj** .

- Debugowanie zoptymalizowanego kodu.

- Debugowanie starej wersji kodu od momentu kompilacji nowej wersji nie powiodło się z powodu błędów kompilacji.

## <a name="see-also"></a>Zobacz także
- [Edytuj i kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Instrukcje: używanie funkcji Edytuj i kontynuuj (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
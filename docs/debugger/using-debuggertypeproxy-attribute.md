---
title: Wyświetlanie typu niestandardowego za pomocą DebuggerTypeProxy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d56d173d715258153f284c55d9bac80c06a50002
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728718"
---
# <a name="tell-the-debugger-what-type-to-show-using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>Poinformuj debugera o typie, który ma być wyświetlany przyC#użyciu atrybutu DebuggerTypeProxy C++(, Visual Basic,/CLI)

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> Określa serwer proxy lub dodatek dla typu i zmienia sposób wyświetlania typu w oknach debugera. Podczas wyświetlania zmiennej, która ma serwer proxy, serwer proxy znajduje się dla oryginalnego typu na **ekranie**. W oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy. Prywatne elementy członkowskie nie są wyświetlane.

Ten atrybut może być stosowany do:

- Struktury
- Klasy
- Zestawy

> [!NOTE]
> W przypadku kodu natywnego ten atrybut jest obsługiwany tylko C++w kodzie/CLI.

Klasa proxy typu musi mieć konstruktora, który przyjmuje argument typu, który zostanie zamieniony na serwer proxy. Debuger tworzy nowe wystąpienie klasy proxy typu za każdym razem, gdy musi wyświetlić zmienną typu docelowego. Może to mieć wpływ na wydajność. W związku z tym nie należy wykonywać więcej pracy w konstruktorze niż absolutnie konieczne.

Aby zminimalizować kary wydajności, ewaluatora wyrażeń nie bada atrybutów na ekranie proxy typu, chyba że typ jest rozwinięty przez użytkownika klikając symbol + w oknie debugera lub przez użycie <xref:System.Diagnostics.DebuggerBrowsableAttribute>. W związku z tym nie należy umieszczać atrybutów dla samego typu wyświetlania. Atrybuty mogą i powinny być używane w treści typu wyświetlania.

Dobrym pomysłem jest, aby typ proxy był prywatną klasą zagnieżdżoną w klasie, do której odwołuje się atrybut. Dzięki temu można łatwo uzyskać dostęp do wewnętrznych członków.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> można odziedziczyć, więc jeśli w klasie podstawowej określono serwer proxy typu, będzie on stosowany do wszystkich klas pochodnych, chyba że klasy pochodne określają własny typ proxy.

Jeśli <xref:System.Diagnostics.DebuggerTypeProxyAttribute> jest używana na poziomie zestawu, parametr `Target` określa typ, który zostanie zamieniony na serwer proxy.

Przykład korzystania z tego atrybutu wraz z <xref:System.Diagnostics.DebuggerDisplayAttribute> i <xref:System.Diagnostics.DebuggerTypeProxyAttribute> można znaleźć w temacie using the[DebuggerDisplay Attribute](../debugger/using-the-debuggerdisplay-attribute.md).

## <a name="using-generics-with-debuggertypeproxy"></a>Używanie typów ogólnych z DebuggerTypeProxy

Obsługa typów ogólnych jest ograniczona. Dla C#programu, `DebuggerTypeProxy` obsługuje tylko typy otwarte. Typ otwarty, nazywany również niekonstruowanym typem, jest typem ogólnym, który nie został skonkretyzowany przy użyciu argumentów dla parametrów typu. Typy zamknięte, nazywane również konstruowanymi typami, nie są obsługiwane.

Składnia typu otwartego wygląda następująco:

`Namespace.TypeName<,>`

W przypadku użycia typu ogólnego jako elementu docelowego w `DebuggerTypeProxy` należy użyć tej składni. Mechanizm `DebuggerTypeProxy` wnioskuje o parametry typu.

Aby uzyskać więcej informacji na temat typów otwartych i C# zamkniętych w temacie zobacz [ C# Specyfikacja języka](/dotnet/csharp/language-reference/language-specification), sekcja 20.5.2 typy otwarte i zamknięte.

Visual Basic nie ma składni typu otwartego, dlatego nie można wykonać tej czynności w Visual Basic. Zamiast tego należy użyć ciągu reprezentującego nazwę typu otwartego.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>Zobacz także

- [Używanie atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-managed-objects.md)
- [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)

---
title: Wyświetlanie typu niestandardowego za pomocą DebuggerTypeProxy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: b98481cb1727ecad9289f63136291d500c0d577e
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85347966"
---
# <a name="tell-the-debugger-what-type-to-show-using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>Poinformuj debugera o typie, który ma być wyświetlany przy użyciu atrybutu DebuggerTypeProxy (C#, Visual Basic, C++/CLI)

<xref:System.Diagnostics.DebuggerTypeProxyAttribute>Określa serwer proxy lub przystawkę dla typu i zmienia sposób wyświetlania typu w oknach debugera. Podczas wyświetlania zmiennej, która ma serwer proxy, serwer proxy znajduje się dla oryginalnego typu na **ekranie**. W oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy. Prywatne elementy członkowskie nie są wyświetlane.

Ten atrybut może być stosowany do:

- Struktury
- Klasy
- Zestawy

> [!NOTE]
> W przypadku kodu natywnego ten atrybut jest obsługiwany tylko w kodzie C++/CLI.

Klasa proxy typu musi mieć konstruktora, który przyjmuje argument typu, który zostanie zamieniony na serwer proxy. Debuger tworzy nowe wystąpienie klasy proxy typu za każdym razem, gdy musi wyświetlić zmienną typu docelowego. Może to mieć wpływ na wydajność. W związku z tym nie należy wykonywać więcej pracy w konstruktorze niż absolutnie konieczne.

Aby zminimalizować kary wydajności, ewaluatora wyrażeń nie bada atrybutów na ekranie proxy typu, chyba że typ jest rozwinięty przez użytkownika, klikając symbol + w oknie debugera lub przez użycie <xref:System.Diagnostics.DebuggerBrowsableAttribute> . W związku z tym nie należy umieszczać atrybutów dla samego typu wyświetlania. Atrybuty mogą i powinny być używane w treści typu wyświetlania.

Dobrym pomysłem jest, aby typ proxy był prywatną klasą zagnieżdżoną w klasie, do której odwołuje się atrybut. Dzięki temu można łatwo uzyskać dostęp do wewnętrznych członków.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute>może być dziedziczona, więc jeśli w klasie podstawowej określono serwer proxy typu, będzie on stosowany do wszystkich klas pochodnych, chyba że klasy pochodne określają swój własny typ proxy.

Jeśli <xref:System.Diagnostics.DebuggerTypeProxyAttribute> jest używana na poziomie zestawu, `Target` parametr określa typ, który zostanie zastąpiony przez serwer proxy.

Przykład korzystania z tego atrybutu wraz z <xref:System.Diagnostics.DebuggerDisplayAttribute> i <xref:System.Diagnostics.DebuggerTypeProxyAttribute> , można znaleźć w temacie[using the DebuggerDisplay Attribute](../debugger/using-the-debuggerdisplay-attribute.md).

## <a name="using-generics-with-debuggertypeproxy"></a>Używanie typów ogólnych z DebuggerTypeProxy

Obsługa typów ogólnych jest ograniczona. Język C# `DebuggerTypeProxy` obsługuje tylko typy otwarte. Typ otwarty, nazywany również niekonstruowanym typem, jest typem ogólnym, który nie został skonkretyzowany przy użyciu argumentów dla parametrów typu. Typy zamknięte, nazywane również konstruowanymi typami, nie są obsługiwane.

Składnia typu otwartego wygląda następująco:

`Namespace.TypeName<,>`

W przypadku użycia typu ogólnego jako elementu docelowego w programie `DebuggerTypeProxy` należy użyć tej składni. `DebuggerTypeProxy`Mechanizm wnioskuje o parametry typu.

Aby uzyskać więcej informacji na temat typów otwartych i zamkniętych w języku C#, zobacz [specyfikację języka c#](/dotnet/csharp/language-reference/language-specification), sekcja 20.5.2 Open i Closed Types.

Visual Basic nie ma składni typu otwartego, dlatego nie można wykonać tej czynności w Visual Basic. Zamiast tego należy użyć ciągu reprezentującego nazwę typu otwartego.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>Zobacz też

- [Używanie atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Tworzenie niestandardowych widoków zarządzanych obiektów](../debugger/create-custom-views-of-managed-objects.md)
- [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)

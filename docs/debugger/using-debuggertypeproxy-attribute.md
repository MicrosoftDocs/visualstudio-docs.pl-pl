---
title: Wyświetlanie typu niestandardowego przy użyciu właściwości DebuggerTypeProxy | Microsoft Docs
description: Użyj wystąpienia DebuggerTypeProxyAttribute, aby określić serwer proxy (element autonomiczny) dla typu, aby zmienić sposób wyświetlania typu w oknach debugera.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 532850f8bb4ac6198481188c2a57a8db15a13873
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389283"
---
# <a name="tell-the-debugger-what-type-to-show-using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>Poinformuj debuger o typie do pokazania przy użyciu atrybutu DebuggerTypeProxy (C#, Visual Basic, C++/CLI)

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> określa serwer proxy lub serwer autonomiczny dla typu i zmienia sposób wyświetlania typu w oknach debugera. Gdy wyświetlasz zmienną, która ma serwer proxy, oznacza on oryginalny typ na **ekranie**. W oknie zmiennej debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy. Prywatne elementy członkowskie nie są wyświetlane.

Ten atrybut można zastosować do:

- Struktury
- Klasy
- Zestawy

> [!NOTE]
> W przypadku kodu natywnego ten atrybut jest obsługiwany tylko w kodzie C++/CLI.

Klasa serwera proxy typu musi mieć konstruktor, który przyjmuje argument typu, który zostanie zastąpiony przez serwer proxy. Debuger tworzy nowe wystąpienie klasy serwera proxy typu za każdym razem, gdy musi wyświetlić zmienną typu docelowego. Może to mieć wpływ na wydajność. W związku z tym nie należy wykonać więcej pracy w konstruktorze niż jest to absolutnie konieczne.

Aby zminimalizować ograniczenia wydajności, ewaluator wyrażeń nie sprawdza atrybutów na serwerze proxy wyświetlania typu, chyba że typ jest rozwijany przez użytkownika klikając symbol + w oknie debugera lub za pomocą polecenia <xref:System.Diagnostics.DebuggerBrowsableAttribute> . W związku z tym nie należy umieszczać atrybutów na typie wyświetlania. Atrybuty mogą i powinny być używane w treści typu wyświetlania.

Dobrym pomysłem jest, aby serwer proxy typu był prywatną klasą zagnieżdżaną w klasie, która jest obiektem docelowym atrybutu. Dzięki temu można łatwo uzyskać dostęp do wewnętrznych elementów członkowskich.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> może być dziedziczony, więc jeśli serwer proxy typu jest określony w klasie bazowej, będzie on miał zastosowanie do wszystkich klas pochodnych, chyba że te klasy pochodne określą własny serwer proxy typu.

Jeśli <xref:System.Diagnostics.DebuggerTypeProxyAttribute> jest używany na poziomie zestawu, parametr określa `Target` typ, który zastąpi serwer proxy.

Aby uzyskać przykład użycia tego atrybutu wraz z atrybutem <xref:System.Diagnostics.DebuggerDisplayAttribute> i , zobacz Using the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> DebuggerDisplay Attribute (Używanie [atrybutu DebuggerDisplay).](../debugger/using-the-debuggerdisplay-attribute.md)

## <a name="using-generics-with-debuggertypeproxy"></a>Używanie typów ogólnych z DebuggerTypeProxy

Obsługa typów ogólnych jest ograniczona. W przypadku języka C# `DebuggerTypeProxy` program obsługuje tylko typy otwarte. Typ otwarty, nazywany również typem bez instrukcji, jest typem ogólnym, który nie został skonstruowany z argumentami dla parametrów typu. Typy zamknięte, nazywane również typami skonstruowanych, nie są obsługiwane.

Składnia typu otwartego wygląda następująco:

`Namespace.TypeName<,>`

Jeśli używasz typu ogólnego jako obiektu docelowego w `DebuggerTypeProxy` programie , musisz użyć tej składni. Mechanizm `DebuggerTypeProxy` wnioskuje o parametrach typu.

Aby uzyskać więcej informacji na temat typów otwartych i zamkniętych w języku C#, zobacz sekcję 20.5.2 Specyfikacja języka [C#,](/dotnet/csharp/language-reference/language-specification)sekcja 20.5.2 Typy otwarte i zamknięte.

Visual Basic nie ma składni typu otwartego, więc nie można zrobić tego samego w Visual Basic. Zamiast tego należy użyć ciągu reprezentacji nazwy typu otwartego.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>Zobacz też

- [Używanie atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-managed-objects.md)
- [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)

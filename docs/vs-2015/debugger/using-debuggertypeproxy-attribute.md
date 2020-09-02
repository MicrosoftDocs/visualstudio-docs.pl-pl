---
title: Używanie atrybutu DebuggerTypeProxy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6e349dd5bea4e0d89c31864960a5438d1e2b13f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684073"
---
# <a name="using-debuggertypeproxy-attribute"></a>Korzystanie z atrybutu DebuggerTypeProxy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DebuggerTypeProxyAttribute —] (assetId:///T: System. Diagnostics. DebuggerTypeProxyAttribute —? qualifyHint = false&autoupgrade = true) Określa serwer proxy lub autonomiczny typ i zmienia sposób wyświetlania typu w oknach debugera. Podczas wyświetlania zmiennej, która ma serwer proxy, serwer proxy znajduje się dla oryginalnego typu na **ekranie**. W oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy. Prywatne elementy członkowskie nie są wyświetlane.  
  
 Ten atrybut może być stosowany do:  
  
- Struktury  
  
- Klasy  
  
- Zestawy  
  
  Klasa proxy typu musi mieć konstruktora, który przyjmuje argument typu, który zostanie zamieniony na serwer proxy. Debuger tworzy nowe wystąpienie klasy proxy typu za każdym razem, gdy musi wyświetlić zmienną typu docelowego. Może to mieć wpływ na wydajność. W związku z tym nie należy wykonywać więcej pracy w konstruktorze niż absolutnie konieczne.  
  
  Aby zminimalizować kary wydajności, ewaluatora wyrażeń nie bada atrybutów na ekranie proxy typu, chyba że typ jest rozwinięty przez użytkownika, klikając symbol + w oknie debugera lub przez użycie <xref:System.Diagnostics.DebuggerBrowsableAttribute> . W związku z tym nie należy umieszczać atrybutów dla samego typu wyświetlania. Atrybuty mogą i powinny być używane w treści typu wyświetlania.  
  
  Dobrym pomysłem jest, aby typ proxy był prywatną klasą zagnieżdżoną w klasie, do której odwołuje się atrybut. Dzięki temu można łatwo uzyskać dostęp do wewnętrznych członków.  
  
  Jeśli <xref:System.Diagnostics.DebuggerTypeProxyAttribute> jest używana na poziomie zestawu, `Target` parametr określa typ, który zostanie zastąpiony przez serwer proxy.  
  
  Przykład korzystania z tego atrybutu wraz z <xref:System.Diagnostics.DebuggerDisplayAttribute> i <xref:System.Diagnostics.DebuggerTypeProxyAttribute> , można znaleźć w temacie[using the DebuggerDisplay Attribute](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## <a name="using-generics-with-debuggertypeproxy"></a>Używanie typów ogólnych z DebuggerTypeProxy  
 Obsługa typów ogólnych jest ograniczona. Język C# `DebuggerTypeProxy` obsługuje tylko typy otwarte. Typ otwarty, nazywany również niekonstruowanym typem, jest typem ogólnym, który nie został skonkretyzowany przy użyciu argumentów dla parametrów typu. Typy zamknięte, nazywane również konstruowanymi typami, nie są obsługiwane.  
  
 Składnia typu otwartego wygląda następująco:  
  
 `Namespace.TypeName<,>`  
  
 W przypadku użycia typu ogólnego jako elementu docelowego w programie `DebuggerTypeProxy` należy użyć tej składni. `DebuggerTypeProxy`Mechanizm wnioskuje o parametry typu.  
  
 Aby uzyskać więcej informacji na temat typów otwartych i zamkniętych w języku C#, zobacz [specyfikację języka c#](https://msdn.microsoft.com/library/e5d5a5cc-636b-4bff-b9c8-a8edc6207c22), sekcja 20.5.2 Open i Closed Types.  
  
 Visual Basic nie ma składni typu otwartego, dlatego nie można wykonać tej czynności w Visual Basic. Zamiast tego należy użyć ciągu reprezentującego nazwę typu otwartego.  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
  [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)

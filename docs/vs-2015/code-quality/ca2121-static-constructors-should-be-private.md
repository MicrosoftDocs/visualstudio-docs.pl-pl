---
title: 'CA2121: konstruktory statyczne powinny być prywatne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f95b33e1391ca755a6c0df261fa2bd05bd3c7a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544316"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Konstruktory statyczne powinny być prywatne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ ma Konstruktor statyczny, który nie jest prywatny.

## <a name="rule-description"></a>Opis reguły
 Konstruktor statyczny, nazywany również konstruktorem klasy, jest używany do inicjowania typu. System wywołuje statyczny konstruktor przed utworzeniem pierwszego wystąpienia typu lub przed odwołaniem do któregokolwiek ze statycznych elementów członkowskich. Użytkownik nie ma kontroli nad tym, kiedy Konstruktor statyczny jest wywoływany. Jeśli konstruktor statyczny nie jest prywatny, może być wywołany przez kod inny niż system. W zależności od operacji, które są wykonywane w konstruktorze, może to spowodować nieoczekiwane zachowanie.

 Ta reguła jest wymuszana przez kompilatory języka C# i Visual Basic platformy .NET.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Naruszenia są zwykle spowodowane przez jedną z następujących akcji:

- Zdefiniowano konstruktora statycznego dla typu i nie został on prywatny.

- Kompilator języka programowania dodał do typu domyślnego konstruktora statycznego i nie uczynić go prywatnym.

  Aby naprawić pierwszy rodzaj naruszenia, ustaw swój statyczny Konstruktor jako prywatny. Aby naprawić drugi rodzaj, Dodaj prywatny statyczny Konstruktor do typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj tych naruszeń. Jeśli projekt oprogramowania wymaga jawnego wywołania konstruktora statycznego, prawdopodobnie projekt zawiera poważne wady i należy go przejrzeć.

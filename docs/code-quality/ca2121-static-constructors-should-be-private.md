---
title: 'CA2121: Konstruktory statyczne powinny być prywatne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 124d65f1147bbc9aa0d38b2bca8f742bf1b60a9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954266"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Konstruktory statyczne powinny być prywatne

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ ma statyczny Konstruktor, który nie jest prywatny.

## <a name="rule-description"></a>Opis reguły

Statyczny Konstruktor, znany także jako konstruktora klasy, jest używany do inicjowania typu. System wywołuje statyczny konstruktor przed utworzeniem pierwszego wystąpienia typu lub przed odwołaniem do któregokolwiek ze statycznych elementów członkowskich. Użytkownik nie ma kontroli nad kiedy wywoływany jest konstruktor statyczny. Jeśli konstruktor statyczny nie jest prywatny, może być wywołany przez kod inny niż system. W zależności od operacji, które są wykonywane w konstruktorze, może to spowodować nieoczekiwane zachowanie.

Ta zasada jest wymuszana przez Kompilatory języka C# i Visual Basic.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Naruszenia zwykle są spowodowane przez jedną z następujących czynności:

- Zdefiniowany Konstruktor statyczny dla danego typu i nie wykonał on prywatnych.

- Kompilator języka programowania dodany statyczny Konstruktor do typu, a nie wykonał on prywatnych.

Aby rozwiązać pierwszy rodzaj naruszenie, upewnij konstruktora statycznego prywatnego. Aby rozwiązać drugi rodzaj, Dodaj Konstruktor statyczny prywatny do danego typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj te naruszenia. Jeśli projekt oprogramowania wymaga jawnym wywołaniem statyczny Konstruktor, jest prawdopodobne, że projekt zawiera poważne wady i powinna zostać przejrzana pod.
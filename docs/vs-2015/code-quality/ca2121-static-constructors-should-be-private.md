---
title: 'CA2121: Konstruktory statyczne powinny być prywatne | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d7894b4ec0039b28a579239605c22c2397c300f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154347"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Konstruktory statyczne powinny być prywatne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 Ta zasada jest wymuszana przez kompilatory języków C# i Visual Basic .NET.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Naruszenia zwykle są spowodowane przez jedną z następujących czynności:

- Zdefiniowany Konstruktor statyczny dla danego typu i nie wykonał on prywatnych.

- Kompilator języka programowania dodany statyczny Konstruktor do typu, a nie wykonał on prywatnych.

  Aby rozwiązać pierwszy rodzaj naruszenie, upewnij konstruktora statycznego prywatnego. Aby rozwiązać drugi rodzaj, Dodaj Konstruktor statyczny prywatny do danego typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj te naruszenia. Jeśli projekt oprogramowania wymaga jawnym wywołaniem statyczny Konstruktor, jest prawdopodobne, że projekt zawiera poważne wady i powinna zostać przejrzana pod.

---
title: 'CA1811: Unikaj niewywołanego kodu prywatnego | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 373ccaa6552079a8995d61ef09bf6e0845c299d6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113524"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Unikaj niewywołanego kodu prywatnego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Prywatne lub wewnętrzne elementu członkowskiego (poziomie zestawu) nie ma obiektów wywołujących w zestawie, nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego i nie jest wywoływany przez delegata. Następujące elementy członkowskie nie są sprawdzane przez tę regułę:

- Elementy członkowskie interfejsu jawnego.

- Konstruktory statyczne.

- Konstruktory serializacji.

- Metody oznaczone atrybutami <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> lub <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

- Elementy członkowskie, które są zastąpień.

## <a name="rule-description"></a>Opis reguły
 Ta zasada można raportów fałszywych alarmów, jeśli wystąpią punkty wejścia, które nie są identyfikowane przez logikę reguł. Ponadto kompilator może emitować Kod noncallable do zestawu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń kod noncallable lub Dodaj kod, który ją wywołuje.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły.

## <a name="related-rules"></a>Powiązane reguły
 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)

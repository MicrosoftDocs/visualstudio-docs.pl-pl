---
title: 'CA2106: potwierdzenia zabezpieczeń | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1f333478c952db74fa6a9482cdad91ce6a858301
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665999"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Potwierdzanie zabezpieczeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda potwierdza uprawnienia i żadne sprawdzenia zabezpieczeń nie są wykonywane na obiekcie wywołującym.

## <a name="rule-description"></a>Opis reguły
 Potwierdzanie uprawnienia zabezpieczeń bez sprawdzania zabezpieczeń może pozostawić zdatną do wykorzystania słabość zabezpieczeń w kodzie. Przeszukiwanie stosu zabezpieczeń jest zatrzymywane, gdy zostanie potwierdzone uprawnienie zabezpieczeń. Jeśli zostanie potwierdzone uprawnienie bez wykonywania żadnych operacji sprawdzania wywołującego, obiekt wywołujący może pośrednio wykonać kod przy użyciu uprawnień. Potwierdzenia bez sprawdzania zabezpieczeń są dozwolone tylko wtedy, gdy masz pewność, że potwierdzenia nie można użyć w sposób szkodliwy. Potwierdzenie jest nieszkodliwe, jeśli wywoływany kod jest nieszkodliwy lub użytkownicy nie mogą przekazać dowolnych informacji do kodu, który jest wywoływany.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać żądanie zabezpieczeń do metody lub jej typu deklarującego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły tylko po dokładnym przeglądzie zabezpieczeń.

## <a name="see-also"></a>Zobacz też
 [zasady bezpiecznego kodowania](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>

---
title: 'CA2145: Metody przezroczyste nie powinny być dekoracyjne z SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d5eb16130aef42abcf9fddf533d0253864a75114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546409"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Metody przezroczyste nie powinny być dekorowane za pomocą atrybutu SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda przezroczysta, metoda oznaczona przy użyciu <xref:System.Security.SecuritySafeCriticalAttribute> metody lub typ, który zawiera metodę, jest oznaczona <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutem.

## <a name="rule-description"></a>Opis reguły
 Metody oznaczone <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutem mają niejawny LinkDemand umieszczany dla każdej metody wywołującej ją. Ten element LinkDemand wymaga, aby kod wywołujący był krytyczny dla bezpieczeństwa. Oznaczenie metody, która używa SuppressUnmanagedCodeSecurity z <xref:System.Security.SecurityCriticalAttribute> atrybutem, sprawia, że to wymaganie jest bardziej oczywiste dla wywołujących metod.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, oznacz metodę lub typ <xref:System.Security.SecurityCriticalAttribute> atrybutem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Komentarze

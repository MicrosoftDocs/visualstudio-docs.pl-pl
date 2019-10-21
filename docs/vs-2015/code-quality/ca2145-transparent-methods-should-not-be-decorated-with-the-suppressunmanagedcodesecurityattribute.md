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
ms.openlocfilehash: 6bffa680fa39014ffa96feec997b5eca63ee08ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610210"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Jawne metody nie powinny być dekorowane za pomocą SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda przezroczysta, metoda oznaczona przy użyciu metody <xref:System.Security.SecuritySafeCriticalAttribute> lub typ, który zawiera metodę, jest oznaczona atrybutem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.

## <a name="rule-description"></a>Opis reguły
 Metody oznaczone atrybutem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> mają niejawny LinkDemand umieszczany w każdej metodzie wywołującej ją. Ten element LinkDemand wymaga, aby kod wywołujący był krytyczny dla bezpieczeństwa. Oznaczenie metody, która używa SuppressUnmanagedCodeSecurity z atrybutem <xref:System.Security.SecurityCriticalAttribute> sprawia, że to wymaganie jest bardziej oczywiste dla wywołujących metod.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, oznacz metodę lub typ z atrybutem <xref:System.Security.SecurityCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Komentarze

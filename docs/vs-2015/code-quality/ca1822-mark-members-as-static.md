---
title: 'CA1822: Oznaczaj składowe jako statyczne | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1cac22ddf4d1f0b61ae176649d562306a4343df7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774355"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Oznaczaj składowe jako statyczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio 2017, zobacz [CA1822: Oznaczaj składowe jako statyczne](https://docs.microsoft.com/visualstudio/code-quality/ca1822-mark-members-as-static) w witrynie docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|MarkMembersAsStatic|  
|CheckId|CA1822|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Podziału non - Jeśli element członkowski nie jest widoczna spoza zestawu, niezależnie od tego, zmiany wprowadzone. Bez podziału — w przypadku tylko zmiany elementu członkowskiego do elementu członkowskiego wystąpienia z `this` — słowo kluczowe.<br /><br /> Przerywanie — Jeśli zmienisz element członkowski z elementu członkowskiego wystąpienia statyczną składową i jest on widoczny spoza zestawu.|  
  
## <a name="cause"></a>Przyczyna  
 Element członkowski, który nie uzyskać dostępu do danych wystąpienia nie jest oznaczony jako statyczne (współużytkowane w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).  
  
## <a name="rule-description"></a>Opis reguły  
 Elementy członkowskie, które nie uzyskuje dostępu do wystąpienia danych lub wywołanie metody wystąpienia mogą zostać oznaczone jako statyczne (współużytkowane w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. Emitowanie niewirtualne wywołania uniemożliwi sprawdzanie w czasie wykonywania dla każdego wywołania, który sprawia, że bieżący wskaźnik do obiektu jest różna od null. Można to osiągnąć wymierny zysk wydajnościowy dla kodu wrażliwego na wydajność. W niektórych przypadkach błąd dostępu do bieżącego wystąpienia obiektu reprezentuje problem poprawności.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Oznacz składową jako statyczną (lub udostępniane w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) lub użyj "this" / "Me" w metodzie body, jeśli to stosowne.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły dla uprzednio wysłane kodu, dla których poprawki będą istotnej zmiany.  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)

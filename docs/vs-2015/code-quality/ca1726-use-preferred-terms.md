---
title: 'CA1726: Używaj preferowanych terminów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e31c459d2d5ce8dc114605716c09f8360eca23d3
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355210"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Używaj preferowanych terminów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1726: Używaj preferowanych terminów](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms) w witrynie docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Istotne — gdy wywoływane zestawów<br /><br /> Podziału non - gdy wywoływane w parametrach typu|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa widocznego na zewnątrz identyfikatora zawiera termin, dla którego istnieje alternatywny, preferowany zamiennik. Alternatywnie nazwa zawiera określenie Flag lub flag.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta reguła analizuje identyfikator na tokeny. Każdy pojedynczy token i ciągłe kombinację dwóch tokenu jest porównywany warunki, które są wbudowane w regule, jak i w sekcji uznane za przestarzałe słowników niestandardowych. W poniższej tabeli przedstawiono warunki, które są wbudowane w zasady i ich preferowany alternatyw.  
  
|Przestarzałe termin|Preferowany termin|  
|-------------------|--------------------|  
|nie są|AreNot|  
|Anulowane|Anulowane|  
|Wprowadzony|Nie można|  
|ComPlus|EnterpriseServices|  
|Nie można|CouldNot|  
|Didnt|DidNot|  
|Numer nie|DoesNot|  
|Dont|DoNot|  
|Flaga lub flag|Nie ma żadnych zastąpienie terminu. Nie używać.|  
|Hadnt|HadNot|  
|Nie|HasNot|  
|jeszcze nie|HaveNot|  
|Indeksy|Indeksy|  
|Isnt|IsNot|  
|Zaloguj się|Logowanie|  
|Wyloguj|Wyloguj|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|Przygotowania|Wyloguj się|  
|Wasnt|WasNot|  
|nie|WereNot|  
|Nie można|WillNot|  
|Wouldnt|WouldNot|  
|Zapisywalny|Zapisywalny|  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, Zamień termin na preferowany termin alternatywny.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomijaj ostrzeżeń dla tej reguły, tylko wtedy, gdy nazwa identyfikatora jest zamierzone i dotyczy oryginalnej termin zamiast preferowany termin.  
  
## <a name="related-rules"></a>Powiązane reguły  
 [Ostrzeżenia dotyczące nazewnictwa](../code-quality/naming-warnings.md)

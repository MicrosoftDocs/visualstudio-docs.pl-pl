---
title: Zarządzany zestaw reguł minimalnego dla kodu zarządzanego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 83f8654a3cca246fa4853add231008e2fadbfc1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667911"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>Zarządzane minimalne reguły dla zarządzanego kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zarządzane reguły minimalne koncentrują się na najważniejszych problemach w kodzie, takich jak potencjalne luki w zabezpieczeniach, awarie aplikacji oraz inne ważne błędy logiki i projektowania. Ten zestaw reguł powinien być dołączany do każdego niestandardowego zestawu reguł tworzonego dla projektów.

|Reguła|Opis|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Usuwaj puste finalizatory|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Pola możliwe do likwidacji należy likwidować|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals|

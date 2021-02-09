---
title: Konstruowanie ciągów filtru dla projektanta tabel | Microsoft Docs
description: Konstruowanie ciągów filtru dla projektanta tabel
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: cdfcacf38239e896687a236624bb167573f4bd1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846208"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Konstruowanie ciągów filtrów dla projektanta tabel
## <a name="overview"></a>Omówienie
Aby filtrować dane w tabeli platformy Azure, która jest wyświetlana w **Projektancie tabel** programu Visual Studio, należy utworzyć ciąg filtru i wprowadzić go w polu filtru. Składnia ciągu filtru jest definiowana przez WCF Data Services i jest podobna do klauzuli SQL WHERE, ale jest wysyłana do Table service za pośrednictwem żądania HTTP. **Projektant tabel** obsługuje odpowiednie kodowanie, dlatego w celu filtrowania według żądanej wartości właściwości należy wprowadzić tylko nazwę właściwości, operator porównania, wartość kryteriów i opcjonalnie operator logiczny w polu filtru. Nie trzeba dołączać opcji zapytania $filter tak samo, jak w przypadku konstruowania adresu URL w celu zbadania tabeli za pośrednictwem [dokumentacji interfejsu API REST usług Storage](/rest/api/storageservices/).

WCF Data Services opierają się na [protokole Open Data Protocol](https://www.odata.org/) (OData). Aby uzyskać szczegółowe informacje na temat opcji filtrowania systemu kwerend (**$Filter**), zobacz [specyfikację identyfikatorów URI usługi OData](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).

## <a name="comparison-operators"></a>Operatory porównania
Następujące operatory logiczne są obsługiwane dla wszystkich typów właściwości:

| Operator logiczny | Opis | Przykładowy ciąg filtru |
| --- | --- | --- |
| eq |Równe |Miasto EQ "Redmond" |
| gt |Większe niż |Cena gt 20 |
| ge |Większe niż lub równe |Cena GE 10 |
| lt |Mniejsze niż |Cena lt 20 |
| le |Mniejsze niż lub równe |Cena Le 100 |
| ne |Nie równa się |Miasto (Londyn) |
| oraz |And |Cena Le 200 i cena gt 3,5 |
| lub |Lub |Cena Le 3,5 lub cena gt 200 |
| not |Not |nie IsAvailable |

Podczas konstruowania ciągu filtru ważne są następujące reguły:

* Operatory logiczne służą do porównywania właściwości z wartością. Należy pamiętać, że nie można porównać właściwości z wartością dynamiczną; jedna ze stron wyrażenia musi być stałą.
* We wszystkich częściach ciągu filtru jest rozróżniana wielkość liter.
* Wartość stała musi mieć ten sam typ danych co właściwość, aby filtr zwracał prawidłowe wyniki. Aby uzyskać szczegółowe informacje na temat obsługiwanych typów właściwości, zobacz [Omówienie modelu danych usługi Table service](/rest/api/storageservices/Understanding-the-Table-Service-Data-Model).

## <a name="filtering-on-string-properties"></a>Filtrowanie właściwości ciągu
W przypadku filtrowania według właściwości ciągu ujmij ciąg w znaki pojedynczego cudzysłowu.

Poniższe przykładowe filtry we właściwościach **PartitionKey** i **RowKey** ; do ciągu filtru można również dodać dodatkowe właściwości niebędące kluczami:

```
PartitionKey eq 'Partition1' and RowKey eq '00001'
```

Każde wyrażenie filtru można ująć w nawiasy, chociaż nie jest to wymagane:

```
(PartitionKey eq 'Partition1') and (RowKey eq '00001')
```

Należy zauważyć, że Table service nie obsługuje zapytań wieloznacznych i nie są obsługiwane w Projektancie tabel. Można jednak wykonać dopasowanie prefiksu przy użyciu operatorów porównania na żądanym prefiksie. Poniższy przykład zwraca jednostki z właściwością LastName rozpoczynającą się literą "A":

```
LastName ge 'A' and LastName lt 'B'
```

## <a name="filtering-on-numeric-properties"></a>Filtrowanie na właściwościach liczbowych
Aby odfiltrować liczbę całkowitą lub zmiennoprzecinkową, określ liczbę bez znaków cudzysłowu.

Ten przykład zwraca wszystkie jednostki z właściwością wieku, której wartość jest większa niż 30:

```
Age gt 30
```

Ten przykład zwraca wszystkie jednostki z właściwością AmountDue, której wartość jest mniejsza lub równa 100,25:

```
AmountDue le 100.25
```

## <a name="filtering-on-boolean-properties"></a>Filtrowanie właściwości logicznych
Aby odfiltrować wartość logiczną, należy określić **wartość PRAWDA** lub **Fałsz** bez znaków cudzysłowu.

Poniższy przykład zwraca wszystkie jednostki, w których właściwość IsActive jest ustawiona na **wartość true**:

```
IsActive eq true
```

Możesz również napisać wyrażenie filtru bez operatora logicznego. W poniższym przykładzie Table service zwróci również wszystkie jednostki, gdzie IsActive jest **prawdziwe**:

```
IsActive
```

Aby zwrócić wszystkie jednostki, w których IsActive ma wartość false, można użyć operatora not:

```
not IsActive
```

## <a name="filtering-on-datetime-properties"></a>Filtrowanie właściwości DateTime
Aby odfiltrować wartość daty i godziny, określ słowo kluczowe **DateTime** , po którym następuje stała Data/godzina w pojedynczym cudzysłowie. Stała Data/godzina musi być w formacie połączonym UTC, zgodnie z opisem w temacie [Formatowanie wartości właściwości DateTime](/rest/api/storageservices/Formatting-DateTime-Property-Values).

Poniższy przykład zwraca jednostki, w których właściwość CustomerSince jest równa 10 lipca 2008:

```
CustomerSince eq datetime'2008-07-10T00:00:00Z'
```

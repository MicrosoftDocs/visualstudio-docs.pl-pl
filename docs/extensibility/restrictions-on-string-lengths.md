---
title: Ograniczenia dotyczące długości ciągów znaków | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df6e068ba612d5e8876e4fa01fbc0751759d5a80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701478"
---
# <a name="restrictions-on-string-lengths"></a>Ograniczenia dotyczące długości ciągów
Interfejs API wtyczki kontroli źródła ogranicza długości ciągów używanych w różnych funkcjach.

## <a name="string-length-values"></a>Wartości długości ciągu

|Stały|Wartość|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> Długość nie obejmuje zakończenia `null`. Inne stałe z przyrostkiem "_SIZE" zamiast "_LEN" zawierają miejsce na zakończenie `null`.

|Stały|Wartość|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)

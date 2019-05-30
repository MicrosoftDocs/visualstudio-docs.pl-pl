---
title: Ograniczenia długości ciągów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab797f76ec6f6118fe4f86a410dbfcfe1e61aa04
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334176"
---
# <a name="restrictions-on-string-lengths"></a>Ograniczenia długości ciągów
Interfejs API wtyczki kontroli źródła ogranicza długości ciągów używanych w różnych funkcji.

## <a name="string-length-values"></a>Wartości długości ciągu

|Stała|Wartość|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> Długość nie obejmuje kończących się `null`. Inne stałych z sufiksem "_rozmiar" zamiast "_LEN" uwzględnić miejsce do zakończenia `null`.

|Stała|Wartość|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Zobacz także
- [Wtyczek kontroli kodu źródłowego](../extensibility/source-control-plug-ins.md)
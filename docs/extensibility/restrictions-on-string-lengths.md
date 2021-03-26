---
title: Ograniczenia dotyczące długości ciągu | Microsoft Docs
description: Dowiedz się więcej na temat limitów długości ciągów używanych przez różne funkcje narzucone przez interfejs API dodatku plug-in kontroli źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b7526494f5d64f7e02e63e5ec3012297af730e87
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068417"
---
# <a name="restrictions-on-string-lengths"></a>Ograniczenia długości ciągu
Interfejs API wtyczki kontroli źródła ogranicza długość ciągów używanych w różnych funkcjach.

## <a name="string-length-values"></a>Wartości długości ciągu

|Stała|Wartość|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> Długość nie obejmuje zakończenia `null` . Inne stałe z sufiksem "_SIZE" zamiast "_LEN" obejmują miejsce dla zakończenia `null` .

|Stała|Wartość|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Zobacz też
- [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)

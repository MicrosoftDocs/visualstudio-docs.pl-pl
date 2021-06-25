---
title: IntelliSenseHostFlags — | Microsoft Docs
description: Wyliczenie IntelliSenseHostFlags określa flagi hosta IntelliSense. W tym artykule opisano wartości wyli roku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 33345f86c69d0faeaa5863534e21eca5ecc176cc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902621"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Określa flagi hosta IntelliSense.

## <a name="syntax"></a>Składnia

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>Parametry

|Elementy członkowskie|Opis|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Bufor kontekstowy jest tylko do odczytu.|
|`IHF_NOSEPARATESUBJECT`|Brak tekstu tematu. Bufor kontekstowy zawiera element docelowy IntelliSense (oznacza `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|Tekst tematu nie jest w stanie wielu wierszach.|
|`IHF_FORCECOMMITTOCONTEXT`|Tak samo jak w przypadku . `CanCommitIntoReadOnlyBuffer`|
|`IHF_OVERTYPE`|Edytowanie (w temacie lub kontekście) powinno odbywać się w trybie zastępowania.|

## <a name="requirements"></a>Wymagania
 SingleFileeditor.idl

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.TextManager.Interop>

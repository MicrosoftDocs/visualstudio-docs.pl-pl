---
title: IntelliSenseHostFlags | Microsoft Docs
description: Wyliczenie IntelliSenseHostFlags określa flagi hosta IntelliSense. W tym artykule opisano wartości wyliczeniowe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b206cc4aa7c1ff388d6868fa8a0533d15da094ff
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487507"
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
|`IHF_READONLYCONTEXT`|Bufor kontekstu jest tylko do odczytu.|
|`IHF_NOSEPARATESUBJECT`|Brak tekstu podmiotu. Bufor kontekstu zawiera funkcję IntelliSense-Target (oznacza `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|Tekst tematu nie jest obsługiwany przez wiele wierszy.|
|`IHF_FORCECOMMITTOCONTEXT`|Analogicznie jak `CanCommitIntoReadOnlyBuffer` .|
|`IHF_OVERTYPE`|Edytowanie (w temacie lub kontekście) powinno odbywać się w trybie zastępowania.|

## <a name="requirements"></a>Wymagania
 SingleFileeditor. idl

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.TextManager.Interop>

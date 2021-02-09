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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af4683dede8a57b2d42acdf357808b465efb1e8e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869508"
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

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.TextManager.Interop>

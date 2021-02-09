---
title: Hierarchia klas typów symboli | Microsoft Docs
description: Przejrzyj listę typów symboli w hierarchii klas zestawu SDK dostępu do interfejsu debugowania programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c33b6852935bbe02c75b0814fd2f77095d283c15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865576"
---
# <a name="class-hierarchy-of-symbol-types"></a>Hierarchia klas typów symboli
W poniższej tabeli opisano typy symboli w hierarchii klas.

## <a name="symbol-types"></a>Typy symboli

|Typ symbolu|Opis|
|-----------------|-----------------|
|[UDT](../../debugger/debug-interface-access/udt.md)|Symbol używany do reprezentowania każdej klasy, struktury i Unii.|
|[Typ wyliczeniowy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Symbol dla typów wyliczeniowych.|
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Symbol dla typów wskaźnika.|
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Symbol dla typów tablicowych.|
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Symbol dla typów podstawowych|
|[Typedef (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Symbol, który wprowadza nazwy dla innych typów.|
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Symbol używany dla każdej klasy bazowej typu zdefiniowanego przez użytkownika (UDT).|
|[Przyjaciel (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Symbol dla zaprzyjaźnionych klas i funkcji zaprzyjaźnionych.|
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Symbol dla każdej unikatowej sygnatury funkcji.|
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Symbol dla każdego parametru do funkcji.|
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Symbol rozmiaru tabeli wirtualnej.|
|[VTable](../../debugger/debug-interface-access/vtable.md)|Symbol tabeli wirtualnej.|
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Symbol dla typu zdefiniowanego przez dostawcę.|
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Symbol typu zdefiniowanego w metadanych.|
|[Wymiar](../../debugger/debug-interface-access/dimension.md)|Symbol dla wymiarów tablicowych.|

> [!NOTE]
> Każdy symbol może mieć właściwości, które zawierają informacje o symbolu, a także odwołania do innych symboli. Te właściwości są wymienione w tematach poszczególnych symboli.

## <a name="see-also"></a>Zobacz też
- [CV_access_e, wyliczenie](../../debugger/debug-interface-access/cv-access-e.md)
- [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Symbole i tagi symboli](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
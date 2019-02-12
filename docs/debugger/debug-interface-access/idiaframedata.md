---
title: IDiaFrameData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData interface
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d710699912a05839ac32c582f40571b04b2de7c2
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56155752"
---
# <a name="idiaframedata"></a>IDiaFrameData
Przedstawia szczegóły ramki stosu.

## <a name="syntax"></a>Składnia

```
IDiaFrameData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
W poniższej tabeli przedstawiono metody `IDiaFrameData`.

|Metoda|Opis|
|------------|-----------------|
|[IDiaFrameData::get_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Pobiera część sekcji adresem kod dla ramki.|
|[IDiaFrameData::get_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Pobiera przesunięcia część adresu kodu dla ramki.|
|[IDiaFrameData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Pobiera obraz wirtualny adres względny (RVA) kod dla ramki.|
|[IDiaFrameData::get_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Pobiera adres wirtualny (oceny luk w zabezpieczeniach) kod dla ramki.|
|[IDiaFrameData::get_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Pobiera długość w bajtach, w bloku kodu opisanego przez ramkę.|
|[IDiaFrameData::get_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|Pobiera liczbę bajtów zmienne lokalne są wypychane na stos.|
|[IDiaFrameData::get_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|Pobiera liczbę bajtów parametrów wypychane na stos.|
|[IDiaFrameData::get_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|Pobiera maksymalną liczbę bajtów wypychane na stos w ramce.|
|[IDiaFrameData::get_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Pobiera liczbę bajtów kod prologu w bloku.|
|[IDiaFrameData::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|Pobiera liczba bajtów zapisanych rejestrów wypychane na stos.|
|[IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Pobiera ciąg program, który jest używany do obliczania rejestru ustawić przed wywołaniem do bieżącej funkcji.|
|[IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Pobiera flagę wskazującą, że obsługi wyjątków systemu jest aktywna.|
|[IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|Pobiera flagę wskazującą, że obsługa wyjątków języka C++ jest włączona.|
|[IDiaFrameData::get_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|Pobiera flagę wskazującą, że blok zawiera punkt wejścia funkcji.|
|[IDiaFrameData::get_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|Pobiera flagę wskazującą, czy podstawowy wskaźnik jest przydzielany dla kodu w tym zakresie adresów. Ta metoda jest przestarzała.|
|[IDiaFrameData::get_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|Pobiera typ ramki specyficznych dla kompilatora.|
|[IDiaFrameData::get_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Pobiera ramki danych interfejsu dla funkcji otaczającej.|
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Wykonuje odwijanie stosu, a następnie zwraca bieżący stan rejestrów w interfejsie ramki przeszukiwania stosu.|

## <a name="remarks"></a>Uwagi
 Szczegóły dostępne dla ramki związanych z punktami wykonania zakresu adresów, wskazywanym przez długość adresu i bloku.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Uzyskanie tego interfejsu, wywołując [idiaenumframedata::Next —](../../debugger/debug-interface-access/idiaenumframedata-next.md) lub [idiaenumframedata::Item —](../../debugger/debug-interface-access/idiaenumframedata-item.md) metody. Zobacz [idiaenumframedata —](../../debugger/debug-interface-access/idiaenumframedata.md) interfejsu, aby uzyskać szczegółowe informacje.

## <a name="example"></a>Przykład
 W tym przykładzie drukuje się właściwości `IDiaFrameData` obiektu. Zobacz [idiaenumframedata —](../../debugger/debug-interface-access/idiaenumframedata.md) interfejsu przykładowy sposób, w jaki `IDiaFrameData` uzyskuje się interfejs.

```C++
void PrintFrameData(IDiaFrameData* pFrameData){
    DWORD dwSect;
    DWORD dwOffset;
    DWORD cbBlock;
    DWORD cbLocals; // Number of bytes reserved for the function locals
    DWORD cbParams; // Number of bytes reserved for the function arguments
    DWORD cbMaxStack;
    DWORD cbProlog;
    DWORD cbSavedRegs;
    BOOL  bSEH;
    BOOL  bEH;
    BOOL  bStart;
    BSTR  wszProgram;

    if(pFrameData->get_addressSection(&dwSect) == S_OK &&
       pFrameData->get_addressOffset(&dwOffset) == S_OK &&
       pFrameData->get_lengthBlock(&cbBlock) == S_OK &&
       pFrameData->get_lengthLocals(&cbLocals) == S_OK &&
       pFrameData->get_lengthParams(&cbParams) == S_OK &&
       pFrameData->get_maxStack(&cbMaxStack) == S_OK &&
       pFrameData->get_lengthProlog(&cbProlog) == S_OK &&
       pFrameData->get_lengthSavedRegisters(&cbSavedRegs) == S_OK &&
       pFrameData->get_systemExceptionHandling(&bSEH) == S_OK &&
       pFrameData->get_cplusplusExceptionHandling(&bEH) == S_OK &&
       pFrameData->get_functionStart(&bStart) == S_OK )
    {
        wprintf(L"Frame address  : %04X:%08X\n", dwSect, dwOffset);
        wprintf(L"Block size     : 0x%8X\n", cbBlock);
        wprintf(L"Locals size    : 0x%8X\n", cbLocals);
        wprintf(L"Parms size     : 0x%8X\n", cbParams);
        wprintf(L"Max stack used : 0x%8X\n", cbMaxStack);
        wprintf(L"Prolog size    : 0x%8X\n", cbProlog);
        wprintf(L"Saved regs size: 0x%8X\n", cbSavedRegs);
        wprintf(L"System Exception Handling: %c\n", bSEH ? L'Y' : L'N');
        wprintf(L"C++ Exception Handling   : %c\n", bEH ? L'Y' : L'N');
        wprintf(L"Function starts in block : %c\n", bStart ? L'Y' : L'N');

        if (pFrameData->get_program(&wszProgram) == S_OK)
        {
            wprintf(L"Program used for register set: %s\n", wszProgram);
            SysFreeString(wszProgram);
        }
        else
        {
            wprintf(L"\n");
        }
    }
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: Dia2.h

Biblioteka: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
[Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
[IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)  
[IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)

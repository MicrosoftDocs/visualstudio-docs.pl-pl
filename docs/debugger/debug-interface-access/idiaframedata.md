---
title: IDiaFrameData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: ee2f68066de6a41e6fd6a1cf4143613a7597d6f1
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467184"
---
# <a name="idiaframedata"></a>IDiaFrameData
Uwidacznia szczegóły ramki stosu.

## <a name="syntax"></a>Składnia

```
IDiaFrameData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
W poniższej tabeli przedstawiono metody `IDiaFrameData` .

|Metoda|Opis|
|------------|-----------------|
|[IDiaFrameData::get_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Pobiera część sekcji adresu kodu dla ramki.|
|[IDiaFrameData::get_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Pobiera część przesunięcia adresu kodu dla ramki.|
|[IDiaFrameData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Pobiera adres wirtualny względem obrazu (RVA) kodu dla ramki.|
|[IDiaFrameData::get_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Pobiera adres wirtualny (VA) kodu dla ramki.|
|[IDiaFrameData::get_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Pobiera długość (w bajtach) bloku kodu opisanego przez ramkę.|
|[IDiaFrameData::get_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|Pobiera liczbę bajtów zmiennych lokalnych wypychanych na stosie.|
|[IDiaFrameData::get_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|Pobiera liczbę bajtów parametrów wypychanych na stosie.|
|[IDiaFrameData::get_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|Pobiera maksymalną liczbę bajtów wypychanych na stosie w ramce.|
|[IDiaFrameData::get_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Pobiera liczbę bajtów kodu prologu w bloku.|
|[IDiaFrameData::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|Pobiera liczbę bajtów zapisanych rejestrów wypchnięcia na stosie.|
|[IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Pobiera ciąg programu, który jest używany do obliczenia zestawu rejestru przed wywołaniem bieżącej funkcji.|
|[IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Pobiera flagę wskazującą, że obsługa wyjątków systemu obowiązuje.|
|[IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|Pobiera flagę wskazującą, że obsługa wyjątków C++ jest włączona.|
|[IDiaFrameData::get_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|Pobiera flagę wskazującą, że blok zawiera punkt wejścia funkcji.|
|[IDiaFrameData::get_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|Pobiera flagę wskazującą, że wskaźnik podstawowy został przydzielony do kodu w tym zakresie adresów. Ta metoda jest przestarzała.|
|[IDiaFrameData::get_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|Pobiera typ ramki specyficznej dla kompilatora.|
|[IDiaFrameData::get_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Pobiera interfejs danych ramek dla otaczającej funkcji.|
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Wykonuje odwinięcia stosu i zwraca bieżący stan rejestrów w interfejsie przeszukiwania stosu.|

## <a name="remarks"></a>Uwagi
 Szczegóły dostępne dla ramki są przeznaczone dla punktów wykonywania w zakresie adresów wskazanym przez adres i długość bloku.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Uzyskaj ten interfejs, wywołując metodę [IDiaEnumFrameData:: Next](../../debugger/debug-interface-access/idiaenumframedata-next.md) lub [IDiaEnumFrameData:: Item](../../debugger/debug-interface-access/idiaenumframedata-item.md) . Aby uzyskać szczegółowe informacje, zobacz Interfejs [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) .

## <a name="example"></a>Przykład
 Ten przykład drukuje właściwości `IDiaFrameData` obiektu. Zobacz interfejs [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) , aby zapoznać się z przykładem sposobu `IDiaFrameData` uzyskiwania interfejsu.

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
Nagłówek: dia2. h

Biblioteka: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)
- [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)

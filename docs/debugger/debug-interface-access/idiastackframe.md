---
title: IDiaStackFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame interface
ms.assetid: 486d25b8-a590-41c1-bdb5-faff3ae35632
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3252d15ebfb06fa840bfad6bf74dc3b8748776ef
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623245"
---
# <a name="idiastackframe"></a>IDiaStackFrame
Udostępnia właściwości ramki stosu.

## <a name="syntax"></a>Składnia

```
IDiaStackFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
Poniżej przedstawiono metod obsługiwanych przez ten interfejs:

|Metoda|Opis|
|------------|-----------------|
|[IDiaStackFrame::get_allocatesBasePointer](../../debugger/debug-interface-access/idiastackframe-get-allocatesbasepointer.md)|Pobiera flagę wskazującą, czy podstawowy wskaźnik jest przydzielany dla kodu w tym zakresie adresów. Ta metoda jest przestarzała.|
|[IDiaStackFrame::get_base](../../debugger/debug-interface-access/idiastackframe-get-base.md)|Pobiera podstawowy adres ramki.|
|[IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)|Pobiera flagę wskazującą, czy obsługa wyjątków języka C++ jest aktywna.|
|[IDiaStackFrame::get_functionStart](../../debugger/debug-interface-access/idiastackframe-get-functionstart.md)|Pobiera flagę wskazującą, że blok zawiera punkt wejścia funkcji.|
|[IDiaStackFrame::get_lengthLocals](../../debugger/debug-interface-access/idiastackframe-get-lengthlocals.md)|Pobiera liczbę bajtów zmienne lokalne są wypychane na stos.|
|[IDiaStackFrame::get_lengthParams](../../debugger/debug-interface-access/idiastackframe-get-lengthparams.md)|Pobiera liczbę bajtów parametrów wypychane na stos.|
|[IDiaStackFrame::get_lengthProlog](../../debugger/debug-interface-access/idiastackframe-get-lengthprolog.md)|Pobiera liczbę bajtów kod prologu w bloku|
|[IDiaStackFrame::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiastackframe-get-lengthsavedregisters.md)|Pobiera liczba bajtów zapisanych rejestrów wypychane na stos.|
|[IDiaStackFrame::get_localsBase](../../debugger/debug-interface-access/idiastackframe-get-localsbase.md)|Pobiera podstawowy adres zmiennych lokalnych.|
|[IDiaStackFrame::get_maxStack](../../debugger/debug-interface-access/idiastackframe-get-maxstack.md)|Pobiera maksymalną liczbę bajtów wypychane na stos w ramce.|
|[IDiaStackFrame::get_rawLVarInstanceValue](../../debugger/debug-interface-access/idiastackframe-get-rawlvarinstancevalue.md)|Pobiera wartość określonej zmiennej lokalnej, jako bajtów raw.|
|[IDiaStackFrame::get_registerValue](../../debugger/debug-interface-access/idiastackframe-get-registervalue.md)|Pobiera wartość określonego rejestru.|
|[IDiaStackFrame::get_returnAddress](../../debugger/debug-interface-access/idiastackframe-get-returnaddress.md)|Pobiera adres zwrotny ramki.|
|[IDiaStackFrame::get_size](../../debugger/debug-interface-access/idiastackframe-get-size.md)|Pobiera rozmiar ramki w bajtach.|
|[IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)|Pobiera flagę wskazującą, system obsługi wyjątków jest aktywna.|
|[IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)|Pobiera typ ramki.|

## <a name="remarks"></a>Uwagi
Ramka stosu jest klasą abstrakcyjną wywołania funkcji podczas jego wykonywania.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Uzyskanie tego interfejsu, wywołując [idiaenumstackframes::Next —](../../debugger/debug-interface-access/idiaenumstackframes-next.md) metody. Zobacz [idiaenumstackframes —](../../debugger/debug-interface-access/idiaenumstackframes.md) interfejsu, na przykład dotyczące uzyskiwania `IDiaStackFrame` interfejsu.

## <a name="example"></a>Przykład
Ten przykład przedstawia różne atrybuty ramki stosu.

```C++
void PrintStackFrame(IDiaStackFrame* pFrame)
{
    if (pFrame != NULL)
    {
        ULONGLONG bottom = 0;
        ULONGLONG top    = 0;

        if (pFrame->get_base(&bottom) == S_OK &&
            pFrame->get_registerValue( CV_REG_ESP, &top ) == S_OK )
        {
            printf("range = 0x%08I64x - 0x%08I64x\n", bottom, top);
        }

        ULONGLONG returnAddress = 0;
        if (pFrame->get_returnAddress(&returnAddress) == S_OK)
        {
            printf("return address = 0x%08I64x\n", returnAddress);
        }

        DWORD lengthFrame     = 0;
        DWORD lengthLocals    = 0;
        DWORD lengthParams    = 0;
        DWORD lengthProlog    = 0;
        DWORD lengthSavedRegs = 0;
        if (pFrame->get_size(&lengthFrame) == S_OK &&
            pFrame->get_lengthLocals(&lengthLocals) == S_OK &&
            pFrame->get_lengthParams(&lengthParams) == S_OK &&
            pFrame->get_lengthProlog(&lengthProlog) == S_OK &&
            pFrame->get_lengthSavedRegisters(&lengthSavedRegs) == S_OK)
        {
            printf("stack frame size          = 0x%08lx bytes\n", lengthFrame);
            printf("length of locals          = 0x%08lx bytes\n", lengthLocals);
            printf("length of parameters      = 0x%08lx bytes\n", lengthParams);
            printf("length of prolog          = 0x%08lx bytes\n", lengthProlog);
            printf("length of saved registers = 0x%08lx bytes\n", lengthSavedRegs);
        }
    }
}
```

## <a name="requirements"></a>Wymagania
Nagłówek: Dia2.h

Biblioteka: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)

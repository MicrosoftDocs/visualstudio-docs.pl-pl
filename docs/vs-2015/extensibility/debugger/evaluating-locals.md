---
title: Ocenianie zmiennych lokalnych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], evaluating locals
- expression evaluation, evaluating locals
ms.assetid: 7d1ed528-4e7a-4d8f-87b4-162440644a75
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e31aa560422c9f18ec30a6e203559ef3ed10c52
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444767"
---
# <a name="evaluating-locals"></a>Ocenianie zmiennych lokalnych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 [Getpropertyinfo —](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) jest wywoływana, aby uzyskać wartości lokalnej, a także lokalnej nazwy i typu. Ponieważ wartość zmiennej lokalnej jest zależny od bieżącego stanu programu, wartości lokalnej musi pochodzić z pamięci. [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) obiekt do powiązania zostanie użyte [IDebugField](../../extensibility/debugger/reference/idebugfield.md) obiekt reprezentujący lokalnej do odpowiedniej lokalizacji w pamięci, zawierającego wartość. Ta lokalizacja w pamięci jest reprezentowany przez [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) obiektu.  
  
 Ta funkcja pobierania wartości zmiennej lokalnej jest hermetyzowany w funkcji pomocnika, która wykonuje następujące zadania:  
  
1. Wiąże `IDebugField` obiektu w pamięci, aby uzyskać `IDebugObject` obiektu.  
  
2. Pobiera wartość z pamięci. Ta wartość jest reprezentowana jako serię bajtów.  
  
3. Formatuje wartość na podstawie typu lokalnego.  
  
4. Zwraca obiekt rodzajowy, zawierający wartość lokalnego. W języku C# to `object`, a w języku C++, to `VARIANT`.  
  
## <a name="managed-code"></a>Kod zarządzany  
 Jest to implementacja funkcji, która pobiera wartości zmiennej lokalnej w kodzie zarządzanym.  
  
```csharp  
namespace EEMC  
{  
    internal class Field  
    {  
        internal static object GetValue(  
            IDebugBinder binder,  
            IDebugField field,  
            Type t,  
            uint size)  
        {  
            if (t == null || size == 0)  return null;  
  
            IDebugObject debugObject = null;  
            binder.Bind(null, field, out debugObject);  
  
            byte[] buffer = new byte[size];  
            for (int i = 0; i < size; i++)  buffer[i] = 0;  
  
            debugObject.GetValue(buffer, size);   
  
            if (t == typeof(sbyte)) return (sbyte) buffer[0];  
            if (t == typeof(short)) return BitConverter.ToInt16(buffer, 0);  
            if (t == typeof(int))   return BitConverter.ToInt32(buffer, 0);  
            if (t == typeof(long))  return BitConverter.ToInt64(buffer, 0);  
            if (t == typeof(byte))  return buffer[0];  
            if (t == typeof(char))  return BitConverter.ToChar(buffer, 0);  
            if (t == typeof(uint))  return BitConverter.ToUInt32(buffer, 0);  
            if (t == typeof(ulong)) return BitConverter.ToUInt64(buffer, 0);  
            if (t == typeof(float)) return BitConverter.ToSingle(buffer, 0);  
            if (t == typeof(double))  return BitConverter.ToDouble(buffer, 0);  
            if (t == typeof(bool))  return BitConverter.ToBoolean(buffer, 0);  
            if (t == typeof(string))  return BitConverter.ToString(buffer, 0);  
            return null;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Niezarządzany kod  
 Jest to implementacja funkcji, która pobiera wartości zmiennej lokalnej w niezarządzanym kodzie. `FieldGetType` jest wyświetlany w [pobieranie wartości lokalnych](../../extensibility/debugger/getting-local-values.md).  
  
```cpp#  
HRESULT FieldGetPrimitiveValue(  
    in  IDebugBinder* pbinder,  
    in  IDebugField*  pfield,  
    out VARIANT*      pvarValue  
    )  
{  
    if (pvarValue == NULL)  
        return E_INVALIDARG;  
    else  
        *pvarValue = 0;  
  
    if (pfield == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    HRESULT hr;  
    UINT          valueSize = 0;  
    BYTE*         pvalueBits = NULL;  
    IDebugObject* pobject    = NULL;  
  
    //get the value as bits  
    hr = pbinder->Bind( NULL, pfield, &pobject );  
    if (FAILED(hr))  
        return hr;  
  
    hr = pobject->GetSize( &valueSize );  
    if (FAILED(hr))  
    {  
        pobject->Release();  
        return hr;  
    }  
  
    pvalueBits = reinterpret_cast<BYTE *>(malloc(valueSize * sizeof(BYTE)));  
    if (!pvalueBits)  
    {  
        pobject->Release();  
        return E_OUTOFMEMORY;  
    }  
  
    hr = pobject->GetValue( pvalueBits, valueSize );  
    pobject->Release();  
    if (FAILED(hr))  
    {  
        free(pvalueBits);  
        return hr;  
    }  
  
    //get the type  
    VARIANT     valueType;  
  
    hr = FieldGetType( pfield, &valueType );  
    if (FAILED(hr))  
    {  
        free(pvalueBits);  
        return hr;  
    }  
  
    //copy a primitive value  
    switch (valueType.vt)  
    {  
    case VT_BSTR:  
        {  
            pvarValue->vt = VT_BSTR;  
            if (valueSize == 0)  
                pvarValue->bstrVal = SysAllocString( OLE("") );  
            else  
                pvarValue->bstrVal =  
                    SysAllocStringByteLen( reinterpret_cast<char*>(pvalueBits),  
                                           valueSize );  
        }  
  
    case VT_BOOL:  
    case VT_I1:  
    case VT_I2:  
    case VT_I4:  
    case VT_I8:  
    case VT_UI1:  
    case VT_UI2:  
    case VT_UI4:  
    case VT_UI8:  
    case VT_R4:  
    case VT_R8:  
        pvarValue->vt = valueType.vt;  
  
        if (valueSize > 8)  
            valueSize = 8;  
        memcpy( &(pvarValue->iVal), pvalueBits, valueSize );  
        break;  
  
    case VT_VOID:  
    case VT_EMPTY:  
        pvarValue->vt = valueType.vt;  
        break;  
  
    default:  
        //not a primitive type  
        VariantClear(&valueType);  
        free(pvalueBits);  
        return E_FAIL;  
    }  
  
    free(pvalueBits);  
    VariantClear(&valueType);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady implementacji zmiennych lokalnych](../../extensibility/debugger/sample-implementation-of-locals.md)   
 [Pobieranie wartości lokalnych](../../extensibility/debugger/getting-local-values.md)   
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)

---
title: IDebugPendingBreakpoint2::CanBind | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::CanBind
helpviewer_keywords:
- IDebugPendingBreakpoint2::CanBind method
- CanBind method
ms.assetid: 84a2b189-ccf1-467e-8fab-0c0da68f0b91
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 07625f7249092e2de3d3dccaaef31a2869755e36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725975"
---
# <a name="idebugpendingbreakpoint2canbind"></a>IDebugPendingBreakpoint2::CanBind
Określa, czy ten oczekujący punkt przerwania może powiązać z lokalizacją kodu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanBind ( 
   IEnumDebugErrorBreakpoints2** ppErrorEnum
);
```

```csharp
int CanBind ( 
   out IEnumDebugErrorBreakpoints2 ppErrorEnum
);
```

## <a name="parameters"></a>Parametry
`ppErrorEnum`\
[na zewnątrz] Zwraca [obiekt IEnumDebugErrorBreakpoints2,](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) który zawiera listę obiektów [IDebugErrorBreakpoint2,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) jeśli mogą wystąpić błędy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK.` powiedzie, zwraca zwraca, `S_FALSE` jeśli punkt przerwania nie `ppErrorEnum` może powiązać, w którym to przypadku błędy są zwracane przez parametr. W przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` wartość, jeśli punkt przerwania został usunięty.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana, aby ustalić, co by się stało, jeśli ten oczekujący punkt przerwania został powiązany. Wywołanie [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) metody faktycznie powiązać oczekujące punktu przerwania.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano, jak `CPendingBreakpoint` zaimplementować tę metodę dla prostego obiektu, który udostępnia interfejs [IDebugPendingBreakpoint2.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

```cpp
HRESULT CPendingBreakpoint::CanBind(IEnumDebugErrorBreakpoints2** ppErrorEnum)
{
   HRESULT hr;
   HRESULT hrT;

   // Check for a valid pointer to an error breakpoint enumerator
   // interface; otherwise, return hr = E_INVALIDARG.
   if (ppErrorEnum)
   {
      // Verify that the pending breakpoint has not been deleted. If
      // deleted, then return hr = E_BP_DELETED.
      if (m_state.state != PBPS_DELETED)
      {
         // Verify that the breakpoint is a file/line breakpoint.
         if (IsFlagSet(m_pBPRequest->m_bpRequestInfo.dwFields, BPREQI_BPLOCATION) &&
             m_pBPRequest->m_bpRequestInfo.bpLocation.bpLocationType == BPLT_CODE_FILE_LINE)
         {
            hr = S_OK;
         }
         // If the breakpoint type is not a file/line breakpoint, then the
         // result should be an error breakpoint.
         else
         {
            // If the error breakpoint member variable does not have
            // allocated memory.
            if (!m_pErrorBP)
            {
               // Create, AddRef, and initialize a CErrorBreakpoint object.
               if (CComObject<CErrorBreakpoint>::CreateInstance(&m_pErrorBP) == S_OK)
               {
                  m_pErrorBP->AddRef();
                  m_pErrorBP->Initialize(this);
               }
            }

            // Create a new enumerator of error breakpoints.
             CComObject<CEnumDebugErrorBreakpoints>* pErrorEnum;
            if (CComObject<CEnumDebugErrorBreakpoints>::CreateInstance(&pErrorEnum) == S_OK)
            {
               // Get the IDebugErrorBreakpoint2 information for the
               // CErrorBreakpoint object.
               CComPtr<IDebugErrorBreakpoint2> spErrorBP;
               hrT = m_pErrorBP->QueryInterface(&spErrorBP);
               assert(hrT == S_OK);
               if (hrT == S_OK)
               {
                  // Initialize the new enumerator of error breakpoints
                  // with the IDebugErrorBreakpoint2 information.
                  IDebugErrorBreakpoint2* rgpErrorBP[] = { spErrorBP.p };
                  hrT = pErrorEnum->Init(rgpErrorBP, &(rgpErrorBP[1]), NULL, AtlFlagCopy);
                  if (hrT == S_OK)
                  {
                     // Verify that the passed IEnumDebugErrorBreakpoints2
                     // interface can be successful queried by the
                     // created CEnumDebugErrorBreakpoints object.
                     hrT = pErrorEnum->QueryInterface(ppErrorEnum);
                     assert(hrT == S_OK);
                  }
               }

               // Otherwise, delete the CEnumDebugErrorBreakpoints object.
               if (FAILED(hrT))
               {
                  delete pErrorEnum;
               }
            }

            hr = S_FALSE;
         }
      }
      else
      {
         hr = E_BP_DELETED;
      }
   }
   else
   {
      hr = E_INVALIDARG;
   }

   return hr;
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

---
title: IDebugBreakpointChecksumRequest2::GetChecksum | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2::GetChecksum
ms.assetid: ec434882-e5c0-4d76-a58b-22c260d8626e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e559b354d231eefcb68052bf660d3618c96ef0b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794728"
---
# <a name="idebugbreakpointchecksumrequest2getchecksum"></a>IDebugBreakpointChecksumRequest2::GetChecksum
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera suma kontrolna dokumentu żądania punktu przerwania podane Unikatowy identyfikator algorytmu sumy kontrolnej do użycia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetChecksum(   
   REFGUID        guidAlgorithm,  
   CHECKSUM_DATA *pChecksumData  
);  
```  
  
```csharp  
public int GetChecksum(   
   ref Guid               guidAlgorithm,  
   out enum_CHECKSUM_DATA pChecksumData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidAlgorithm`  
 [in] Unikatowy identyfikator algorytmu sumy kontrolnej.  
  
 `pChecksumData`  
 [out] Suma kontrolna dokumentu dla żądania punktu przerwania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
 Funkcja, która sprawdza, czy suma kontrolna dokumentu, które ma być powiązana, jest zgodna z interfejsu użytkownika można znaleźć w poniższym przykładzie.  
  
```cpp#  
bool CDebugProgram::DoChecksumsMatch(CDebugPendingBreakpoint *pPending, CDebugCodeContext *pContext)  
{  
    bool fRet = false;  
    HRESULT hRes;  
  
    // Get the checksum for the document we are about to bind to from the pdb side  
    GUID guidAlgorithmId;  
    BYTE *pChecksum = NULL;  
    ULONG cNumBytes = 0;  
  
    hRes = pContext->GetDocumentChecksumAndAlgorithmId(&guidAlgorithmId, &pChecksum, &cNumBytes);  
  
    if ( S_OK == hRes )  
    {  
        // Get checksum data for the document from the UI (request) side  
        CComPtr<IDebugBreakpointChecksumRequest2> pChecksumRequest;  
  
        hRes = pPending->GetChecksumRequest(&pChecksumRequest);  
  
        if ( S_OK == hRes )  
        {  
            CHECKSUM_DATA data;  
  
            hRes = pChecksumRequest->GetChecksum(guidAlgorithmId, &data);  
  
            if ( S_OK == hRes )  
            {  
                if ( data.ByteCount == cNumBytes && memcmp(data.pBytes, pChecksum, cNumBytes) == 0 )  
                    fRet = true;  
                else  
                    fRet = false;  
  
                // Free up data allocated for checksum data  
                CoTaskMemFree(data.pBytes);  
            }  
            else  
                fRet = true; // checksums not available - user disabed checksums  
        }  
        else  
            fRet = true; // we couldn't get checksum from UI - default to past behavior  
  
        // free up space allocated for checksum from pdb  
        CoTaskMemFree(pChecksum);  
    }  
    else  
        fRet = true; // we don't have a checksum to compare with.  
  
    return ( fRet );  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)


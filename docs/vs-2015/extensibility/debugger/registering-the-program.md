---
title: Rejestrowanie programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31d03f12a31953cbc0e20d06820dd49b5f9827e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824547"
---
# <a name="registering-the-program"></a>Rejestrowanie programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po uzyskaniu przez aparat debugowania portu reprezentowanego przez interfejs [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , następnym krokiem w celu debugowania programu jest zarejestrowanie go z portem. Po zarejestrowaniu program jest dostępny do debugowania przy użyciu jednej z następujących metod:  
  
- Proces dołączania, który umożliwia debugerowi uzyskanie pełnej kontroli debugowania działającej aplikacji.  
  
- Debugowanie just-in-Time (JIT), które umożliwia debugowanie po wystąpieniu programu uruchamianego niezależnie od debugera. Gdy architektura środowiska uruchomieniowego przechwytuje błąd, debuger zostanie powiadomiony, zanim system operacyjny lub środowisko uruchomieniowe zwolni pamięć i zasoby programu powodującego błąd.  
  
## <a name="registering-procedure"></a>Procedura rejestrowania  
  
#### <a name="to-register-your-program"></a>Aby zarejestrować program  
  
1. Wywołaj metodę [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) zaimplementowaną przez port.  
  
     `IDebugPortNotify2::AddProgramNode` wymaga wskaźnika do interfejsu [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .  
  
     Zwykle, gdy system operacyjny lub środowisko uruchomieniowe ładuje program, tworzy węzeł Program. Jeśli aparat debugowania (DE) zostanie poproszony o załadowanie programu, program utworzy i zarejestruje węzeł programu.  
  
     Poniższy przykład pokazuje aparat debugowania uruchamiający program i rejestrując go z portem.  
  
    > [!NOTE]
    > Nie jest to jedyny sposób uruchomienia i wznowienia procesu; jest to głównie przykład rejestracji programu z portem.  
  
    ```cpp#  
    // This is an IDebugEngineLaunch2 method.  
    HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                          IDebugPort2 *pPort,  
                                          /* omitted parameters */,  
                                          IDebugProcess2**ppDebugProcess)  
    {  
        // do stuff here to set up for a launch (such as handling the other parameters)  
        ...  
  
        // Now get the IPortNotify2 interface so we can register a program node  
        // in CDebugEngine::ResumeProcess.  
        CComPtr<IDebugDefaultPort2> spDefaultPort;  
        HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
        if (SUCCEEDED(hr))  
        {  
            CComPtr<IDebugPortNotify2> spPortNotify;  
            hr = spDefaultPort->GetPortNotify(&spPortNotify);  
            if (SUCCEEDED(hr))  
            {  
                // Remember the port notify so we can use it in ResumeProcess.  
                m_spPortNotify = spPortNotify;  
  
                // Now launch the process in a suspended state and return the  
                // IDebugProcess2 interface  
                CComPtr<IDebugPortEx2> spPortEx;  
                hr = pPort->QueryInterface(&spPortEx);  
                if (SUCCEEDED(hr))  
                {  
                    // pass on the parameters we were given (omitted here)  
                    hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)  
                }  
            }  
        }  
        return(hr);  
    }  
  
    HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
    {  
        // Make a program node for this process  
        HRESULT hr;  
        CComPtr<IDebugProgramNode2> spProgramNode;  
        hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            hr = m_spPortNotify->AddProgramNode(spProgramNode);  
            if (SUCCEEDED(hr))  
            {  
                // resume execution of the process using the port given to us earlier.  
               // (Querying for the IDebugPortEx2 interface is valid here since  
               // that's how we got the IDebugPortNotify2 interface in the first place.)  
                CComPtr<IDebugPortEx2> spPortEx;  
                hr = m_spPortNotify->QueryInterface(&spPortEx);  
                if (SUCCEEDED(hr))  
                {  
                    hr  = spPortEx->ResumeProcess(pDebugProcess);  
                }  
            }  
        }  
        return(hr);  
    }  
  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie portu](../../extensibility/debugger/getting-a-port.md)   
 [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

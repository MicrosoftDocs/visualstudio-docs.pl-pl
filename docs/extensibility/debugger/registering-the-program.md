---
title: Rejestrowanie programu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60bc94efb9d3b2026de31c6018b466d432bf98f8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315959"
---
# <a name="register-the-program"></a>Rejestrowanie programu
Po aparat debugowania uzyskała portu, reprezentowane przez [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfejsu, następnym krokiem podczas włączania debugowania programu jest zarejestrowanie go za pomocą portu. Po zarejestrowaniu programu jest dostępna do debugowania za pomocą jednej z następujących sposobów:

- Proces dołączania, która pozwala debugerowi na przejęcie kontroli debugowania z działającej aplikacji.

- Just-in-time (JIT) debugowania, który pozwala na debugowanie po fakcie program, który działa niezależnie od debugera. Architektura środowiska wykonawczego przechwytuje usterki, Debuger jest powiadamiany przed systemu operacyjnego lub środowisko uruchomieniowe zwalnia pamięć i zasoby programu łagodne.

## <a name="registering-procedure"></a>Rejestrowanie procedury

### <a name="to-register-your-program"></a>Aby zarejestrować program

1. Wywołaj [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) metody implementowane przez port.

     `IDebugPortNotify2::AddProgramNode` wymaga aby wskazywał [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu.

     Zazwyczaj podczas ładowania programu systemie operacyjnym lub w środowisku uruchomieniowym tworzy węzeł program. Jeśli aparat debugowania (Niemcy) jest pytanie, aby załadować program, DE tworzącego i rejestrującego węzła programu.

     Aparat debugowania, uruchamiając program i rejestrując ją za pomocą portu można znaleźć w poniższym przykładzie.

    > [!NOTE]
    > Ten przykładowy kod nie jest jedynym sposobem, aby uruchomić i wznowić procesu; Ten kod jest głównie przykładem rejestrowania programu z portem.

    ```cpp
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

## <a name="see-also"></a>Zobacz także
- [Pobieranie portu](../../extensibility/debugger/getting-a-port.md)
- [Włączanie programu do debugowania](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
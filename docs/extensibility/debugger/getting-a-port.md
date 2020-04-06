---
title: Uzyskiwanie portu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bf4948e7cb2590136774eab76fbafec91dbfa40
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738628"
---
# <a name="get-a-port"></a>Uzyskaj port
Port reprezentuje połączenie z komputerem, na którym są uruchomione procesy. To urządzenie może być komputerem lokalnym lub zdalnym (który może być uruchomiony system operacyjny nieoparty na systemie Windows; zobacz [Porty,](../../extensibility/debugger/ports.md) aby uzyskać więcej informacji).

Port jest reprezentowany przez interfejs [IDebugPort2.](../../extensibility/debugger/reference/idebugport2.md) Służy do uzyskiwania informacji o procesach uruchomionych na komputerze, do którego jest podłączony port.

Aparat debugowania potrzebuje dostępu do portu w celu zarejestrowania węzłów programu z portem i spełnienia żądań informacji o procesie. Na przykład jeśli aparat debugowania implementuje interfejs [IDebugProgramProvider2,](../../extensibility/debugger/reference/idebugprogramprovider2.md) implementacja [metody GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) może poprosić port o zwrócenie niezbędnych informacji o procesie.

Visual Studio dostarcza niezbędny port do aparatu debugowania i uzyskuje ten port od dostawcy portu. Jeśli program jest dołączony do (albo z wewnątrz debugera lub z powodu wyjątku został zgłoszony, który wyzwala just-in-time [JIT] okno dialogowe), użytkownik ma możliwość wyboru transportu (inna nazwa dostawcy portu) do użycia. W przeciwnym razie jeśli użytkownik uruchamia program z poziomu debugera, system projektu określa dostawcę portu do użycia. W obu przypadkach visual studio wystąpienia dostawcy portu, reprezentowane przez interfejs [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) i prosi o nowy port, wywołując [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) z interfejsem [IDebugPortRequest2.](../../extensibility/debugger/reference/idebugportrequest2.md) Ten port jest następnie przekazywany do aparatu debugowania w takiej czy innej formie.

## <a name="example"></a>Przykład
Ten fragment kodu pokazuje, jak użyć portu dostarczonego do [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) zarejestrować węzeł programu w [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Dla jasności pominięto parametry niezwiązane bezpośrednio z tą koncepcją.

> [!NOTE]
> W tym przykładzie użyto portu do uruchomienia i wznowienia procesu i zakłada, że interfejs [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) jest zaimplementowany na porcie. W żadnym wypadku nie jest to jedyny sposób wykonywania tych zadań i jest możliwe, że port nie może być nawet zaangażowany w inne niż [iDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) programu.

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
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>Zobacz też
- [Rejestracja programu](../../extensibility/debugger/registering-the-program.md)
- [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)
- [Porty](../../extensibility/debugger/ports.md)

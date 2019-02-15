---
title: Pobieranie portu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3967dc1b324c2dd73de4797588159d745ae24756
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315719"
---
# <a name="get-a-port"></a>Pobieranie portu
Port reprezentuje połączenie z maszyną, na którym są uruchomione procesy. Tego komputera może być komputer lokalny lub zdalny komputer (który może potencjalnie być systemem operacyjnym systemem Windows; zobacz [porty](../../extensibility/debugger/ports.md) Aby uzyskać więcej informacji).

Port jest reprezentowany przez [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfejsu. Jest on używany do uzyskiwania informacji na temat procesów uruchomionych na komputerze, który port jest podłączony do.

Aparat debugowania wymaga dostępu do portu, aby zarejestrować program węzłów z portem i do spełnienia żądania informacji o procesie. Na przykład, jeśli aparat debugowania implementuje [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) interfejsu, wykonania na [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metoda zadawać port na potrzeby procesu informacje, które mają zostać zwrócone.

Program Visual Studio dostarcza niezbędne portu do debugowania do aparatu i uzyskuje ten port z dostawcy portu. Jeśli program jest dołączony do (lub z w ramach debugera ze względu na wyjątek został zgłoszony, która wyzwala okno dialogowe Just-in-Time [JIT]), użytkownik może wskazać wybór transportu (inną nazwę dla dostawcy portu) do użycia. W przeciwnym razie, jeśli użytkownik uruchamia program z w ramach debugera, system projektu określa dostawcy portu do użycia. W obu przypadkach program Visual Studio tworzy wystąpienie dostawcy portu, reprezentowane przez [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfejs i prosi o nowy port, przez wywołanie metody [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) z [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) interfejsu. Ten port jest następnie przekazywany do aparatu debugowania w postaci jednego lub drugiego.

## <a name="example"></a>Przykład
Ten fragment kodu przedstawia sposób użycia portu dostarczane do [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) można zarejestrować węzła programu w [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Parametry nie są bezpośrednio związane z tę koncepcję zostały pominięte dla przejrzystości.

> [!NOTE]
> W tym przykładzie używa portu do uruchomienia i wznowić proces i zakłada się, że [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) interfejs jest implementowany przy użyciu portu. W żadnym wypadku nie jest to jedyny sposób wykonywania tych zadań i jest możliwe, że port nie nawet zajmuje innych niż program [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) nadane jej.

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

## <a name="see-also"></a>Zobacz także
[Rejestrowanie programu](../../extensibility/debugger/registering-the-program.md)  
[Włączanie programu do debugowania](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
[Dostawcy portów](../../extensibility/debugger/port-suppliers.md)  
[Porty](../../extensibility/debugger/ports.md)

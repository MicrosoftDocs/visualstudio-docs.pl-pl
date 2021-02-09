---
title: Pobieranie portu | Microsoft Docs
description: Dowiedz się, w jaki sposób program Visual Studio dostarcza port do aparatu debugowania, aby zarejestrować węzły programu z portem i spełnić żądania dotyczące informacji o procesie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f3ee9c145a4c6275f64d357d87ac1cc284bfac6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921295"
---
# <a name="get-a-port"></a>Pobierz port
Port reprezentuje połączenie z komputerem, na którym są uruchomione procesy. Może to być maszyna lokalna lub maszyna zdalna (w przypadku których może być uruchomiony system operacyjny inny niż Windows). Aby uzyskać więcej informacji, zobacz [porty](../../extensibility/debugger/ports.md) .

Port jest reprezentowany przez interfejs [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) . Służy do uzyskiwania informacji o procesach uruchomionych na komputerze, z którym jest połączony port.

Silnik debugowania wymaga dostępu do portu, aby zarejestrować węzły programu z portem i spełnić żądania dotyczące informacji o procesie. Na przykład jeśli aparat debugowania implementuje interfejs [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) , implementacja metody [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) może zażądać portu do zwrócenia informacji o niezbędnych procesach.

Program Visual Studio dostarcza wymagany port do aparatu debugowania i uzyskuje ten port od dostawcy portów. Jeśli program jest dołączony do (w debugerze lub wystąpił wyjątek, który wyzwala okno dialogowe just-in-Time [JIT]), użytkownik otrzymuje wybór transportu (inna nazwa dla dostawcy portów) do użycia. W przeciwnym razie, jeśli użytkownik uruchamia program w debugerze, system projektu określa dostawcę portów do użycia. W każdym z tych zdarzeń program Visual Studio tworzy wystąpienie dostawcy portu reprezentowanego przez interfejs [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) i pyta o nowy port, wywołując metodę [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) z interfejsem [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) . Ten port jest następnie przeszedł do aparatu debugowania w jednej postaci lub innej.

## <a name="example"></a>Przykład
Ten fragment kodu przedstawia sposób użycia portu dostarczonego do [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) w celu zarejestrowania węzła programu w [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Parametry, które nie są bezpośrednio związane z tym pojęciem, zostały pominięte w celu przejrzystości.

> [!NOTE]
> W tym przykładzie używa się portu do uruchomienia i wznowienia procesu i zakłada, że interfejs [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) jest zaimplementowany na porcie. Nie oznacza to, że jedynym sposobem wykonania tych zadań jest to, że port może nie być nawet związany z [IDebugProgramNode2em](../../extensibility/debugger/reference/idebugprogramnode2.md) programu.

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
- [Rejestrowanie programu](../../extensibility/debugger/registering-the-program.md)
- [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)
- [Porty](../../extensibility/debugger/ports.md)

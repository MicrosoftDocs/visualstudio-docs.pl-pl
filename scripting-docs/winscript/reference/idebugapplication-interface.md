---
title: Interfejs IDebugApplication | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8229f234f8a8ce607f36c48e070cb3d40a211d45
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58152473"
---
# <a name="idebugapplication-interface"></a>Interfejs IDebugApplication
Przedstawia-remote metody debugowania do użytku przez język aparatów i hosty.  
  
 Oprócz metod odziedziczone `IRemoteDebugApplication`, `IDebugApplication` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Ustawia nazwę aplikacji.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Powiadamia Menedżer debugowania procesów, że aparat języka, w trybie pojedynczego kroku zostanie powrócić do obiektu wywołującego.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Powoduje, że dany ciąg mają być wyświetlane przez debuger środowiska IDE.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Uruchamia domyślny debuger środowiska IDE i dołącza sesji debugowania do tej aplikacji, jeśli nie jest już dołączony.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Powoduje, że bieżący wątek zablokować, a następnie wysyła powiadomienie z informacją o punkt przerwania do debugera w IDE.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Powoduje, że ta aplikacja jest zwolnienie wszystkich odwołań, a następnie wprowadź nieaktywny.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Zwraca bieżące flagi przerwania dla aplikacji.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Zwraca wątek skojarzony z aktualnie uruchomionemu wątkowi.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Zapewnia dostęp asynchronicznych operacji danego synchroniczne debugowania.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Dodaje dostawcę moduł wyliczający ramek stosu do tej aplikacji.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Usuwa dostawcę moduł wyliczający ramek stosu z tej aplikacji.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Określa, czy bieżący wątek uruchomionego wątku debugera.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Udostępnia mechanizm do obiektu wywołującego uruchomić kod w wątku debugera.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Tworzy nowy węzeł aplikacji, który jest skojarzony z dostawcą danego dokumentu.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Wyzwala zdarzenie generyczne do debugera `IApplicationDebugger` interfejsu.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Powoduje, że bieżący wątek zablokować, a następnie wysyła powiadomienie z informacją o błędzie do debugera w IDE.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Określa, czy debuger just in time (JIT) jest zarejestrowany.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Określa, czy jest debugera JIT jest zarejestrowana w celu bez hostów auto-debug.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Dodaje dostawcę kontekstu wyrażenie globalne do tej aplikacji.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Usuwa dostwcy kontekstu wyrażenie globalne z tej aplikacji.|
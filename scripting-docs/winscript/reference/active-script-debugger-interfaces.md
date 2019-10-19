---
title: Interfejsy debugera aktywnego skryptu | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger interfaces
- activdbg.h
ms.assetid: bf4750b1-4e58-442b-ab56-254e640de61d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 477374d93e4d8d5139197dcd49fef0e930e5ff32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572699"
---
# <a name="active-script-debugger-interfaces"></a>Interfejsy debugera aktywnego skryptu
Pliki nagłówkowe activdbg. h i activdbg100. h zapewniają interfejsy, wyliczenia i struktury wymienione w tej sekcji. Są one przeznaczone do debugowania skryptów.  
  
> [!NOTE]
> Interfejsy `IJSDebug*` i interfejs `IEnumJsStackFrames` zostały najpierw wydane w programie Internet Explorer 11 do debugowania kodu natywnego za pomocą skryptu. Plik nagłówkowy dla tych interfejsów to Jscript9diag. h.  
  
## <a name="in-this-section"></a>W tej sekcji  
 Następujące interfejsy zezwalają na niezależny od języka, debugowanie neutralne od hosta:  
  
- [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
- [IActiveScriptDebug, interfejs](../../winscript/reference/iactivescriptdebug-interface.md)  
  
- [IActiveScriptErrorDebug, interfejs](../../winscript/reference/iactivescripterrordebug-interface.md)  
  
- [IActiveScriptErrorDebug110, interfejs](../../winscript/reference/iactivescripterrordebug110-interface.md)  
  
- [IActiveScriptSiteDebug, interfejs](../../winscript/reference/iactivescriptsitedebug-interface.md)  
  
- [IActiveScriptSiteDebug32, interfejs](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
  
- [IActiveScriptSiteDebugEx, interfejs](../../winscript/reference/iactivescriptsitedebugex-interface.md)  
  
- [IActiveScriptWinRTErrorDebug, interfejs](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)  
  
- [IApplicationDebugger, interfejs](../../winscript/reference/iapplicationdebugger-interface.md)  
  
- [IApplicationDebuggerUI, interfejs](../../winscript/reference/iapplicationdebuggerui-interface.md)  
  
- [IDebugApplication, interfejs](../../winscript/reference/idebugapplication-interface.md)  
  
- [IDebugApplication110, interfejs](../../winscript/reference/idebugapplication110-interface.md)  
  
- [IDebugApplicationNode, interfejs](../../winscript/reference/idebugapplicationnode-interface.md)  
  
- [IDebugApplicationNode100, interfejs](../../winscript/reference/idebugapplicationnode100-interface.md)  
  
- [IDebugApplicationNodeEvents, interfejs](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
  
- [IDebugApplicationThread, interfejs](../../winscript/reference/idebugapplicationthread-interface.md)  
  
- [IDebugApplicationThread110, interfejs](../../winscript/reference/idebugapplicationthread110-interface.md)  
  
- [IDebugApplicationThreadEvents110, interfejs](../../winscript/reference/idebugapplicationthreadevents110-interface.md)  
  
- [IDebugAsyncOperation, interfejs](../../winscript/reference/idebugasyncoperation-interface.md)  
  
- [IDebugAsyncOperationCallBack, interfejs](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
  
- [IDebugCodeContext, interfejs](../../winscript/reference/idebugcodecontext-interface.md)  
  
- [IDebugCookie, interfejs](../../winscript/reference/idebugcookie-interface.md)  
  
- [IDebugDocument, interfejs](../../winscript/reference/idebugdocument-interface.md)  
  
- [IDebugDocumentContext, interfejs](../../winscript/reference/idebugdocumentcontext-interface.md)  
  
- [IDebugDocumentHelper, interfejs](../../winscript/reference/idebugdocumenthelper-interface.md)  
  
- [IDebugDocumentHost, interfejs](../../winscript/reference/idebugdocumenthost-interface.md)  
  
- [IDebugDocumentInfo, interfejs](../../winscript/reference/idebugdocumentinfo-interface.md)  
  
- [IDebugDocumentProvider, interfejs](../../winscript/reference/idebugdocumentprovider-interface.md)  
  
- [IDebugDocumentText, interfejs](../../winscript/reference/idebugdocumenttext-interface.md)  
  
- [IDebugDocumentTextAuthor, interfejs](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
  
- [IDebugDocumentTextEvents, interfejs](../../winscript/reference/idebugdocumenttextevents-interface.md)  
  
- [IDebugDocumentTextExternalAuthor, interfejs](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)  
  
- [IDebugExpression, interfejs](../../winscript/reference/idebugexpression-interface.md)  
  
- [IDebugExpressionCallBack, interfejs](../../winscript/reference/idebugexpressioncallback-interface.md)  
  
- [IDebugExpressionContext, interfejs](../../winscript/reference/idebugexpressioncontext-interface.md)  
  
- [IDebugFormatter, interfejs](../../winscript/reference/idebugformatter-interface.md)  
  
- [IDebugHelper, interfejs](../../winscript/reference/idebughelper-interface.md)  
  
- [IDebugSessionProvider, interfejs](../../winscript/reference/idebugsessionprovider-interface.md)  
  
- [IDebugSessionProviderEx, interfejs](../../winscript/reference/idebugsessionproviderex-interface.md)  
  
- [IDebugStackFrame, interfejs](../../winscript/reference/idebugstackframe-interface.md)  
  
- [IDebugStackFrameSniffer, interfejs](../../winscript/reference/idebugstackframesniffer-interface.md)  
  
- [IDebugStackFrameSnifferEx, interfejs](../../winscript/reference/idebugstackframesnifferex-interface.md)  
  
- [IDebugSyncOperation, interfejs](../../winscript/reference/idebugsyncoperation-interface.md)  
  
- [IDebugThreadCall, interfejs](../../winscript/reference/idebugthreadcall-interface.md)  
  
- [IEnumDebugApplicationNodes, interfejs](../../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  
- [IEnumDebugCodeContexts, interfejs](../../winscript/reference/ienumdebugcodecontexts-interface.md)  
  
- [IEnumDebugExpressionContexts, interfejs](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  
- [IEnumDebugStackFrames, interfejs](../../winscript/reference/ienumdebugstackframes-interface.md)  
  
- [IEnumJsStackFrames, interfejs](../../winscript/reference/ienumjsstackframes-interface.md)  
  
- [IEnumRemoteDebugApplications, interfejs](../../winscript/reference/ienumremotedebugapplications-interface.md)  
  
- [IEnumRemoteDebugApplicationThreads, interfejs](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  
- [IJsDebug, interfejs](../../winscript/reference/ijsdebug-interface.md)  
  
- [IJsDebugBreakPoint, interfejs](../../winscript/reference/ijsdebugbreakpoint-interface.md)  
  
- [IJsDebugDataTarget, interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)  
  
- [IJsDebugFrame, interfejs](../../winscript/reference/ijsdebugframe-interface.md)  
  
- [IJsDebugProcess, interfejs](../../winscript/reference/ijsdebugprocess-interface.md)  
  
- [IJsDebugProperty, interfejs](../../winscript/reference/ijsdebugproperty-interface.md)  
  
- [IJsDebugStackWalker, interfejs](../../winscript/reference/ijsdebugstackwalker-interface.md)  
  
- [IJsEnumDebugProperty, interfejs](../../winscript/reference/ijsenumdebugproperty-interface.md)  
  
- [IMachineDebugManager, interfejs](../../winscript/reference/imachinedebugmanager-interface.md)  
  
- [IMachineDebugManagerCookie, interfejs](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
  
- [IMachineDebugManagerEvents, interfejs](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
  
- [IProcessDebugManager, interfejs](../../winscript/reference/iprocessdebugmanager-interface.md)  
  
- [IProvideExpressionContexts, interfejs](../../winscript/reference/iprovideexpressioncontexts-interface.md)  
  
- [IRemoteDebugApplication, interfejs](../../winscript/reference/iremotedebugapplication-interface.md)  
  
- [IRemoteDebugApplication110, interfejs](../../winscript/reference/iremotedebugapplication110-interface.md)  
  
- [IRemoteDebugApplicationEx, interfejs](../../winscript/reference/iremotedebugapplicationex-interface.md)  
  
- [IRemoteDebugApplicationEvents, interfejs](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
  
- [IRemoteDebugApplicationThread, interfejs](../../winscript/reference/iremotedebugapplicationthread-interface.md)  
  
- [IRemoteDebugApplicationThreadEx, interfejs](../../winscript/reference/iremotedebugapplicationthreadex-interface.md)  
  
- [ISetNextStatement, interfejs](../../winscript/reference/isetnextstatement-interface.md)  
  
- [ISimpleConnectionPoint, interfejs](../../winscript/reference/isimpleconnectionpoint-interface.md)  
  
- [IWebAppDiagnosticsSetup, interfejs](../../winscript/reference/iwebappdiagnosticssetup-interface.md)  
  
- [IWebAppDiagnosticsObjectInitialization, interfejs](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)  
  
  W poniższej sekcji wymieniono stałe, wyliczenia i struktury używane do debugowania:  
  
- [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Przegląd debugowania aktywnego skryptu](../../winscript/active-script-debugging-overview.md)
---
title: Implementowanie interfejsów pomocnika inteligentnego hosta | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: deac5827aa38039099f1d0f5e621d473db96743d
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835605"
---
# <a name="implementing-smart-host-helper-interfaces"></a>Implementacja interfejsów pomocnika inteligentnego hosta
Interfejs [interfejsu IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md) znacznie upraszcza zadanie tworzenia inteligentnego hosta na potrzeby aktywnego debugowania, ponieważ zapewnia implementacje dla wielu interfejsów, które są niezbędne do hostingu inteligentnego.  
  
 Aby być hostem inteligentnym przy użyciu programu `IDebugDocumentHelper` , aplikacja hosta musi mieć tylko trzy rzeczy:  
  
1. `CoCreate`Program Process Debug Manager i używa interfejsu [interfejsu IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md) , aby dodać aplikację do listy aplikacji możliwością debugowania.  
  
2. Utwórz pomocnika dokumentu debugowania dla każdego obiektu skryptu, używając metody [IProcessDebugManager:: CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) . Upewnij się, że zdefiniowano nazwę dokumentu, dokument nadrzędny, tekst i bloki skryptów.  
  
3. Zaimplementuj Interfejs [interfejsu IActiveScriptSiteDebug](../winscript/reference/iactivescriptsitedebug-interface.md) w obiekcie, który implementuje interfejs [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) (który jest wymagany w przypadku aktywnych skryptów). Jedyną nieprostą metodą w `IActiveScriptSiteDebug` interfejsie jest po prostu delegata do pomocnika.  
  
   Opcjonalnie host może zaimplementować interfejs [interfejsu IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) , jeśli potrzebuje dodatkowej kontroli nad kolorem składni, tworzeniem kontekstu dokumentu i innymi funkcjami dodatkowymi.  
  
   Głównym ograniczeniem pomocnika inteligentnego hosta jest, że może on obsłużyć tylko dokumenty, których zawartość zmienia się lub zmniejsza po ich dodaniu (chociaż dokumenty mogą zostać rozwinięte). Jednak w przypadku wielu hostów inteligentnych funkcjonalność, którą zapewnia, jest dokładnie to, co jest potrzebne.  
  
   W poniższych sekcjach szczegółowo omówiono każdy krok.  
  
## <a name="create-an-application-object"></a>Tworzenie obiektu aplikacji  
 Aby można było użyć pomocnika inteligentnego hosta, należy utworzyć obiekt [interfejsu IDebugApplication](../winscript/reference/idebugapplication-interface.md) , aby reprezentować aplikację w debugerze.  
  
#### <a name="to-create-an-application-object"></a>Aby utworzyć obiekt aplikacji  
  
1. Utwórz wystąpienie Menedżera debugowania procesów przy użyciu polecenia `CoCreateInstance` .  
  
2. Wywołaj metodę [IProcessDebugManager::](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3. Ustaw nazwę aplikacji przy użyciu [IDebugApplication:: SetName](../winscript/reference/idebugapplication-setname.md).  
  
4. Dodaj obiekt aplikacji do listy aplikacji możliwością debugowania za pomocą [IProcessDebugManager:: addapplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     Poniższy kod przedstawia proces, ale nie obejmuje sprawdzania błędów ani innych niezawodnych technik programistycznych.  
  
    ```cpp
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>Korzystanie z IDebugDocumentHelper  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>Aby użyć pomocnika (minimalnej sekwencji kroków)  
  
1. Dla każdego dokumentu hosta Utwórz pomocnika przy użyciu [IProcessDebugManager:: CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2. Wywołanie [IDebugDocumentHelper:: init](../winscript/reference/idebugdocumenthelper-init.md) na Pomocniku, podanie nazwy, atrybutu dokumentu i tak dalej.  
  
3. Call [IDebugDocumentHelper:: Attach](../winscript/reference/idebugdocumenthelper-attach.md) z pomocnikiem nadrzędnym dla dokumentu (lub wartość null, jeśli dokument jest elementem głównym), aby zdefiniować położenie dokumentu w drzewie i uczynić go widocznym dla debugera.  
  
4. Wywołanie [IDebugDocumentHelper:: AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) lub [IDebugDocumentHelper:: AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) w celu zdefiniowania tekstu dokumentu. (Mogą one być wywoływane wielokrotnie, jeśli dokumenty są pobierane przyrostowo, tak jak w przypadku przeglądarki).  
  
5. Call [IDebugDocumentHelper::D efinescriptblock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) do definiowania zakresów dla każdego bloku skryptu i skojarzonych aparatów skryptów.  
  
## <a name="implementing-iactivescriptsitedebug"></a>Implementowanie IActiveScriptSiteDebug  
 Aby zaimplementować [IActiveScriptSiteDebug:: GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), Pobierz pomocnika odpowiadającego danej lokacji, a następnie Pobierz przesunięcie dokumentu początkowego dla danego kontekstu źródłowego w następujący sposób:  
  
```cpp
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Następnie użyj pomocnika, aby utworzyć nowy kontekst dokumentu dla danego przesunięcia znaku:  
  
```cpp
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Aby zaimplementować [IActiveScriptSiteDebug:: GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md), po prostu wywołaj metodę `IDebugApplication::GetRootNode` (Odziedziczone z [IRemoteDebugApplication:: GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)).  
  
 Aby zaimplementować [IDebugDocumentHelper:: GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md), po prostu zwróć `IDebugApplication` wcześniej utworzone za pomocą Menedżera debugowania procesów.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>Opcjonalny interfejs IDebugDocumentHost  
 Host może zapewnić implementację [interfejsu IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) za pomocą [IDebugDocumentHelper:: SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) w celu zapewnienia dodatkowej kontroli nad pomocnikiem. Poniżej przedstawiono niektóre kluczowe możliwości interfejsu hosta, które umożliwiają wykonywanie następujących czynności:  
  
- Dodaj tekst za pomocą [IDebugDocumentHelper:: AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) , aby host nie musiał bezpośrednio podawać rzeczywistych znaków. Gdy znaki są naprawdę potrzebne, pomocnik wywoła [IDebugDocumentHost:: GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) na hoście.  
  
- Przesłoń domyślne kolorowanie składni dostarczone przez pomocnika. Pomocnik wywołuje [IDebugDocumentHost:: GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) , aby określić kolorowanie dla zakresu znaków, powracając do jego domyślnej implementacji, jeśli zwraca hosta `E_NOTIMPL` .  
  
- Podaj kontrolkę nieznaną dla kontekstów dokumentu utworzonych przez pomocnika, implementując [IDebugDocumentHost:: OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md). Umożliwia to hostowi przesłonięcie funkcjonalności implementacji domyślnego kontekstu dokumentu.  
  
- Podaj nazwę ścieżki w systemie plików dla dokumentu. Niektóre interfejsów użytkownika debugowania używają tego, aby umożliwić użytkownikowi edytowanie i zapisywanie zmian w dokumencie. [IDebugDocumentHost:: NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) jest wywoływana w celu powiadomienia hosta po zapisaniu dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd debugowania aktywnego skryptu](../winscript/active-script-debugging-overview.md)
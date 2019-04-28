---
title: Implementacja interfejsów pomocnika inteligentnego hosta | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9a5b94a25a838845acab2ce1c49295b0b28d425
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976193"
---
# <a name="implementing-smart-host-helper-interfaces"></a>Implementacja interfejsów pomocnika inteligentnego hosta
[Interfejs IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md) interfejsu znacznie upraszcza zadanie tworzenia hosta inteligentnego dla aktywnego debugowania, ponieważ zawiera implementacje dla wielu interfejsów wymaganych do hostowania inteligentnych.  
  
 Jako host inteligentny przy użyciu `IDebugDocumentHelper`, aplikacji hosta, należy wykonać tylko trzy rzeczy:  
  
1. `CoCreate` Menedżer debugowania procesów, a następnie użyj [interfejs IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md) interfejsu, aby dodać aplikację do listy debugowania aplikacji.  
  
2. Utwórz pomocnika dokumentu debugowania dla każdego skryptu obiektu przy użyciu [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) metody. Upewnij się, że nazwy dokumentu, dokument nadrzędny, tekst i bloki skryptu są zdefiniowane.  
  
3. Implementowanie [interfejs IActiveScriptSiteDebug](../winscript/reference/iactivescriptsitedebug-interface.md) interfejsu na obiekt, który implementuje [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) interfejsu (wymagane jest wykonywanie aktywnych skryptów). Tylko nieuproszczony metodę na `IActiveScriptSiteDebug` interfejsu po prostu deleguje odpowiednie uprawnienia do elementu pomocniczego.  
  
   Opcjonalnie można wdrożyć hosta [interfejs IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) interfejsu, jeśli potrzebny dodatkową kontrolę nad kolor składni, tworzenia kontekstu dokumentów i innych rozszerzoną funkcjonalność.  
  
   Głównym ograniczeniem związanym na pomocnika inteligentnego hosta jest, że tylko może obsłużyć dokumentów, których zawartość, zmienić lub Zmniejsz po ich dodaniu (mimo że dokumenty można rozwinąć). W przypadku wielu hostów inteligentnych jednak funkcjonalność, którą zapewnia jest dokładnie co jest potrzebne.  
  
   W poniższych sekcjach opisano każdy krok bardziej szczegółowo.  
  
## <a name="create-an-application-object"></a>Utwórz obiekt aplikacji  
 Przed użyciem pomocnika inteligentnego hosta jest niezbędne do utworzenia [interfejs IDebugApplication](../winscript/reference/idebugapplication-interface.md) obiektu do reprezentowania Twojej aplikacji w debugerze.  
  
#### <a name="to-create-an-application-object"></a>Aby utworzyć obiekt aplikacji  
  
1. Utwórz wystąpienie obiektu debugowania procesu przy użyciu Menedżera `CoCreateInstance`.  
  
2. Wywołaj [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3. Ustaw nazwę aplikacji przy użyciu [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md).  
  
4. Dodawanie obiektu aplikacji do listy debugowania aplikacji za pomocą [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     Poniższy kod przedstawia proces, ale nie obejmuje sprawdzanie błędów lub innymi technikami programowania niezawodne.  
  
    ```cpp
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>Za pomocą IDebugDocumentHelper  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>Aby użyć pomocnika (minimalny sekwencji kroków)  
  
1. Dla każdego dokumentu hosta, należy utworzyć przy użyciu Pomocnika [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2. Wywołaj [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) na pomocnika, podając nazwę, atrybuty dokumentu i tak dalej.  
  
3. Wywołaj [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) przy użyciu Pomocnika nadrzędnym dla dokumentu (lub wartość NULL, jeśli dokument jest katalogiem głównym) do definiowania położenie dokumentu w drzewie i była widoczna dla debugera.  
  
4. Wywołaj [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) lub [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) do definiowania tekst dokumentu. (Te można wywołać wiele razy, jeśli dokument zostanie pobrana przyrostowo, tak jak w przypadku przeglądarki.)  
  
5. Wywołaj [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) zdefiniować zakresów dla każdego bloku skryptu i aparatów skryptów skojarzonych.  
  
## <a name="implementing-iactivescriptsitedebug"></a>Implementing IActiveScriptSiteDebug  
 Aby zaimplementować [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), Pobierz pomocnika odpowiadający danej lokacji, a następnie pobierać dokumentu startowego przesunięcie w kontekście danego źródła w następujący sposób:  
  
```cpp
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Następnie użyj pomocnika, aby utworzyć nowy kontekst dokumentu przesunięcia dany znak:  
  
```cpp
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Aby zaimplementować [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md), wystarczy wywołać `IDebugApplication::GetRootNode` (odziedziczone [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)).  
  
 Aby zaimplementować [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md), po prostu zwrot `IDebugApplication` początkowo utworzony za pomocą Menedżer debugowania procesów.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>Opcjonalny interfejs IDebugDocumentHost  
 Host może dostarczać implementację [interfejs IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md) przy użyciu [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) zapewnienie dodatkowej kontroli nad pomocnika. Oto kilka kluczowych kwestii, które interfejs hosta pozwala robić:  
  
- Dodaj tekst przy użyciu [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) tak, aby hosta nie jest konieczne natychmiastowe Podaj rzeczywiste znaki. W razie znaki są naprawdę wywoła Pomocnika [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) na hoście.  
  
- Zastąp domyślną kolorowanie składni, dostarczone przez pomocnika. Wywołania Pomocnika [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) ustalenie kolorowanie dla zakresu znaków, nastąpi powrót na jego implementacji domyślnej, jeśli zwróci hosta `E_NOTIMPL`.  
  
- Podaj kontrolowanie nieznane kontekstów dokument utworzony przez pomocnika, implementując [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md). Dzięki temu hosta do przesłonięcia funkcji Domyślna implementacja kontekstu dokumentu.  
  
- Podaj nazwę ścieżki systemu plików dla dokumentu. Niektóre debugowania interfejsów użytkownika służy do umożliwienia użytkownikowi edytowanie i zapisywanie zmian w dokumencie. [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) jest wywoływana w celu powiadomienia hosta, po zapisaniu dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd debugowania aktywnego skryptu](../winscript/active-script-debugging-overview.md)
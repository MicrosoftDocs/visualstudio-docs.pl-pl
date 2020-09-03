---
title: Udostępnianie kontekstu usługi językowej przy użyciu starszego interfejsu API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4471b71b612008ba7d0733c92286415cd3c3f6b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193870"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Dostarczanie kontekstu usługi językowej za pomocą starszego interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dostępne są dwie opcje usługi językowej umożliwiające udostępnianie kontekstu użytkownika przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podstawowego edytora: Podaj kontekst znacznika tekstu lub podaj wszystkie konteksty użytkownika. Różnice między poszczególnymi elementami zostały opisane w tym miejscu.  
  
 Aby uzyskać więcej informacji na temat dostarczania kontekstu do usługi językowej, która jest połączona z własnym edytorem, zobacz [How to: zapewnianie kontekstu dla edytorów](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Podaj kontekst znacznika tekstu dla edytora  
 Aby zapewnić kontekst błędów kompilatora wskazanych przez znaczniki tekstu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Edytorze podstawowym, zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfejs. W tym scenariuszu Usługa językowa udostępnia kontekst tylko wtedy, gdy kursor znajduje się na znaczniku tekstowym. Dzięki temu Edytor może dostarczyć słowo kluczowe w kursorze do okna **Pomoc dynamiczna** bez atrybutów.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Podaj wszystkie konteksty użytkownika do edytora  
 Jeśli tworzysz usługę językową i korzystasz z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podstawowego edytora, możesz zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interfejs w celu zapewnienia kontekstu dla usługi językowej.  
  
 Do wdrożenia programu `IVsLanguageContextProvider` , zbiór kontekstowy (kolekcja) jest dołączony do edytora, który jest odpowiedzialny za aktualizowanie zbioru kontekstowego. Gdy **dynamiczne okno pomocy** wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> interfejs w tym zbiorze kontekstu w czasie bezczynności, zbiór kontekstu wysyła zapytanie do edytora w celu uzyskania aktualizacji. Następnie Edytor powiadamia usługę języka, że powinna zaktualizować Edytor, i przekazuje wskaźnik do zbioru kontekstowego. W tym celu należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> metodę z edytora do usługi językowej. Korzystając ze wskaźnika do zbioru kontekstowego, usługa języka może teraz dodawać i usuwać atrybuty i słowa kluczowe. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Istnieją dwa różne sposoby implementacji `IVsLanguageContextProvider` :  
  
- Podaj słowo kluczowe dla zbioru kontekstowego  
  
   Po wywołaniu edytora w celu zaktualizowania zbioru kontekstu należy przekazać odpowiednie słowa kluczowe i atrybuty, a następnie zwrócić `S_OK` . Ta wartość zwracana nakazuje edytorowi zachowanie słowa kluczowego i kontekstu atrybutów zamiast podania słowa kluczowego do zbioru kontekstowego.  
  
- Uzyskaj słowo kluczowe ze słowa kluczowego przy kursorze  
  
   Po wywołaniu edytora w celu zaktualizowania zbioru kontekstu należy przekazać odpowiednie atrybuty, a następnie zwrócić `E_FAIL` . Ta wartość zwracana powoduje, że Edytor zachowuje atrybuty w zbiorze kontekstowym, ale aktualizuje zbiór kontekstowy za pomocą słowa kluczowego na kursora.  
  
  Na poniższym diagramie przedstawiono, jak kontekst jest udostępniany dla usługi języka implementującej `IVsLanguageContextProvider` .  
  
  ![Grafika LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  Kontekst usługi językowej  
  
  Jak widać na diagramie, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podstawowy edytor tekstów ma dołączony zbiór kontekstowy. Ten zbiór kontekstu wskazuje trzy oddzielne torby kontekstu: usługa językowa, edytor domyślny i znacznik tekstu. Torby kontekstu usług językowych i tekstowych zawierają atrybuty i słowa kluczowe dla usługi językowej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> , jeśli interfejs jest zaimplementowany, i znaczniki tekstu, jeśli <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interfejs jest zaimplementowany. Jeśli żaden z tych interfejsów nie zostanie wdrożony, Edytor zawiera kontekst słowa kluczowego na kursorze w domyślnym zestawie kontekstu edytora.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Wskazówki dotyczące kontekstu dla edytorów i projektantów  
 Projektanci i edytory muszą podawać ogólne słowo kluczowe dla edytora lub okna projektanta. Dzieje się tak, aby w przypadku, gdy użytkownik naciśnie klawisz F1, będzie wyświetlał ogólny, ale odpowiedni temat pomocy dla projektanta lub edytora. Edytor musi, oprócz tego, podać bieżące słowo kluczowe przy kursorze lub podać kluczowy termin na podstawie bieżącego zaznaczenia. W tym celu należy się upewnić, że temat pomocy dla elementu tekstowego lub interfejsu użytkownika jest wyświetlany lub zaznaczony, gdy użytkownik naciśnie klawisz F1. Projektant dostarcza kontekst dla elementu wybranego w projektancie, takiego jak przycisk w formularzu. Redaktorzy i projektanci muszą także połączyć się z usługą językową, jak opisano w [starszej wersji usługi językowej](../extensibility/internals/legacy-language-service-essentials.md).

---
title: 'Instrukcje: Debugowanie niestandardowego aparatu debugowania | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5292d2cde8a75a239f7a905d8cf5d80b09a8f61e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753908"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Instrukcje: Debugowanie niestandardowego aparatu debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Typ projektu spowoduje uruchomienie aparatu debugowania (DE) z <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> metody. Oznacza to, że DE jest uruchamiane pod kontrolą programu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kontrolowanie tego typu projektu. Jednak to wystąpienie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nie można debugować DE. Poniżej przedstawiono kroki umożliwiające debugować swoje niestandardowe DE.  
  
> [!NOTE]
>  :     W procedurze "Debugowanie niestandardowego debugowanie aparatu" należy poczekać DE do uruchomienia, zanim będzie możliwe dołączenie do niej. Jeśli na początku swoje DE, który jest wyświetlany, gdy rozpoczyna się DE okno komunikatu, możesz dołączyć w tym momencie, a następnie wyczyść okno komunikatu, aby kontynuować. W ten sposób możesz przechwytywać wszystkie zdarzenia DE.  
  
> [!WARNING]
>  Konieczne jest posiadanie zdalne debugowanie, przed rozpoczęciem poniższej procedury. Zobacz [zdalne debugowanie](../../debugger/remote-debugging.md) Aby uzyskać szczegółowe informacje.  
  
### <a name="debugging-a-custom-debug-engine"></a>Debugowanie niestandardowego aparatu debugowania  
  
1.  Rozpocznij msvsmon.exe, monitora debugowania zdalnego.  
  
2.  Z **narzędzia** w msvsmon.exe, wybierz opcję menu **opcje** otworzyć **opcje** okno dialogowe.  
  
3.  Wybierz opcję "Brak uwierzytelniania", a następnie kliknij przycisk **OK**.  
  
4.  Uruchom wystąpienie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , a następnie otwórz projekt DE niestandardowych.  
  
5.  Uruchom drugie wystąpienie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , a następnie otwórz Twojego własnego projektu, który uruchamia DE (do tworzenia aplikacji, zazwyczaj jest to w gałęzi rejestru eksperymentalnych, skonfigurowany po zainstalowaniu VSIP).  
  
6.  W tym drugim przypadku [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], ładowanie pliku źródłowego z Twojego własnego projektu i uruchom program do debugowania. Zaczekaj kilka minut, aby umożliwić DE do załadowania lub poczekaj, aż zostanie osiągnięty punkt przerwania.  
  
7.  W pierwszym wystąpieniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (za pomocą projektu DE), wybierz **dołączyć do procesu** z **debugowania** menu.  
  
8.  W **dołączyć do procesu** okno dialogowe, zmiana **transportu** do **zdalny (natywny tylko bez uwierzytelniania)**.  
  
9. Zmiana **kwalifikator** nazwę komputera (Uwaga: dostępna jest Historia wpisów, więc trzeba wpisywać w nazwie to tylko raz).  
  
10. W **dostępne procesy** , wybierz wystąpienie usługi DE, która jest uruchomiona i kliknij pozycję na liście **Dołącz** przycisku.  
  
11. Po symbole zostały załadowane w swojej DE, należy umieścić punkty przerwania w kodzie DE.  
  
12. Za każdym razem, aby zatrzymać i ponownie uruchom proces debugowania, powtórz kroki od 6 do 10.  
  
### <a name="debugging-a-custom-project-type"></a>Typ niestandardowego projektu debugera  
  
1.  Rozpocznij [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] w gałęzi rejestru normalne i obciążenia projektu wpisz projektu (jest to, źródło, aby typem projektu, nie podczas tworzenia wystąpienia tego typu projektu).  
  
2.  Otwórz właściwości projektu i przejdź do **debugowania** strony. Aby uzyskać **polecenia**, wpisz ścieżkę do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (domyślnie jest to *[dysk]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe).  
  
3.  Aby uzyskać **argumenty wiersza polecenia**, typ `/rootsuffix exp` gałęzi rejestru eksperymentalne (utworzone podczas instalacji VSIP).  
  
4.  Kliknij przycisk **OK** aby zatwierdzić zmiany.  
  
5.  Uruchomić swój typ projektu, naciskając klawisz F5. Spowoduje to uruchomienie drugie wystąpienie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
6.  W tym momencie można umieścić punkty przerwania w kodzie źródłowym typu projektu.  
  
7.  W drugim wystąpieniu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], obciążenia, lub Utwórz nowe wystąpienie tego typu projektu. Podczas tworzenia lub obciążenia są osiągane punktów przerwania.  
  
8.  Debuguj typu projektu.  
  
9. Jeśli chcesz debugować proces uruchamiania DE, można wykonać kroki opisane w procedurze "Debugowanie niestandardowego debugowanie aparatu", aby dołączyć do swojej DE, po jego uruchomieniu. Zapewni to trzy wystąpienia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uruchomiona: jeden dla typu źródła danych projektu, drugie dla typów projektów wystąpień i trzecią dołączona do Twojej DE.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)

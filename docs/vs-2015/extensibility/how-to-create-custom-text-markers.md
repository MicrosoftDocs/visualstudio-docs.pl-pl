---
title: 'Instrukcje: Tworzenie niestandardowych znaczników tekstu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780963"
---
# <a name="how-to-create-custom-text-markers"></a>Instrukcje: tworzenie niestandardowych znaczników tekstu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli chcesz utworzyć niestandardowy znacznik tekstu, aby wyróżnić lub zorganizować kod, musisz wykonać następujące czynności:  
  
- Rejestrowanie nowego znacznika tekstu, dzięki czemu inne narzędzia mogą uzyskać do niego dostęp  
  
- Podaj domyślną implementację i konfigurację znacznika tekstu  
  
- Tworzenie usługi, która może być używana przez inne procesy w celu użycia znacznika tekstu  
  
  Aby uzyskać szczegółowe informacje na temat stosowania znacznika tekstu do regionu kodu, zobacz [How to: use Text Marks](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Aby zarejestrować znacznik niestandardowy  
  
1. Utwórz wpis rejestru w następujący sposób:  
  
    HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \Text Editor\External — znaczniki\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID></em>jest `GUID` używany do identyfikowania dodawanego znacznika  
  
    *\<Version>* jest wersją programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , na przykład 8,0  
  
    *\<PackageGUID>* jest identyfikatorem GUID pakietu VSPackage implementującego obiekt automatyzacji.  
  
   > [!NOTE]
   > Ścieżka katalogu głównego HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* może być zastąpiona alternatywnym katalogiem głównym po zainicjowaniu powłoki Visual Studio, aby uzyskać więcej informacji, zobacz [przełączniki wiersza polecenia](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Utwórz cztery wartości w obszarze HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \Text Editor\External\\*\<MarkerGUID>*  
  
   - (Domyślnie)  
  
   - Usługa  
  
   - Nazwa wyświetlana  
  
   - Pakiet  
  
   - `Default` jest opcjonalnym wpisem typu REG_SZ. Po ustawieniu wartość wpisu jest ciągiem zawierającym przydatne informacje identyfikujące, na przykład "znacznik tekstu niestandardowego".  
  
   - `Service` to wpis typu REG_SZ zawierający ciąg identyfikatora GUID usługi, która zapewnia niestandardowy znacznik tekstu według proffering <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> . Format to {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
   - `DisplayName` to wpis typu REG_SZ zawierający identyfikator zasobu nazwy niestandardowego znacznika tekstu. Format jest #YYYY.  
  
   - `Package` jest wpisem typu REG_SZ zawierającego `GUID` pakietu VSPackage, który dostarcza usługę wymienioną w obszarze usługa. Format to {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>Aby utworzyć niestandardowy znacznik tekstu  
  
1. Zaimplementuj interfejs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>.  
  
     Twoja implementacja tego interfejsu definiuje zachowanie i wygląd typu znacznika niestandardowego.  
  
     Ten interfejs jest wywoływany, gdy  
  
    1. Użytkownik uruchamia środowisko IDE po raz pierwszy.  
  
    2. Użytkownik wybiera przycisk **Resetuj ustawienia domyślne** na stronie właściwości **czcionki i kolory** w folderze **Environment** , znajdującym się w lewym okienku okna dialogowego **Opcje** uzyskanym w menu **Narzędzia** środowiska IDE.  
  
2. Zaimplementuj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> metodę, określając, która `IVsPackageDefinedTextMarkerType` implementacja powinna zostać zwrócona na podstawie identyfikatora GUID typu znacznika określonego w wywołaniu metody.  
  
     Środowisko wywołuje tę metodę podczas pierwszego tworzenia typu znacznika niestandardowego i określa identyfikator GUID identyfikujący typ znacznika niestandardowego.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Aby udąło typ znacznika jako usługę  
  
1. Wywoływanie <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> metody dla <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> .  
  
     Wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> jest zwracany.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> metodę, określając identyfikator GUID identyfikujący typ niestandardowego znacznika usługi i dostarczając wskaźnik do implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interfejsu. <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>Implementacja powinna zwrócić wskaźnik do implementacji <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> interfejsu.  
  
     Unikatowy plik cookie wskazujący, że usługa jest zwracana. Później możesz użyć tego pliku cookie do odwoływania usługi niestandardowego typu znaczników przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metody <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfejsu określającej tę wartość pliku cookie.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie znaczników tekstowych ze starszym interfejsem API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Instrukcje: Dodawanie standardowych znaczników tekstu](../extensibility/how-to-add-standard-text-markers.md)   
 [Instrukcje: implementowanie znaczników błędów](../extensibility/how-to-implement-error-markers.md)   
 [Instrukcje: korzystanie ze znaczników tekstu](../extensibility/how-to-use-text-markers.md)

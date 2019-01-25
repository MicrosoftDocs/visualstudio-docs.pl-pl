---
title: Tworzenie składników Web Part programu SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Microsoft.SharePoint.WebControls.DateTimeControl
- Microsoft.SharePoint.WebControls.CssLink
- Microsoft.SharePoint.WebControls.RssLink
- Microsoft.SharePoint.WebControls.Theme
- Microsoft.SharePoint.WebControls.AspMenu
- Microsoft.SharePoint.WebControls.ListProperty
- Microsoft.SharePoint.WebControls.ProjectProperty
- Microsoft.SharePoint.WebControls.FormsDigest
- Microsoft.SharePoint.WebControls.ScriptLink
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web Parts
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eff779f70cb5b17d03befddce971a4bbb15ca142
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865892"
---
# <a name="create-web-parts-for-sharepoint"></a>Tworzenie składników web Part programu SharePoint
  Za pomocą składników web Part, można zmodyfikować zawartość, wygląd i zachowanie stron witryny programu SharePoint za pomocą przeglądarki. Części sieci Web to formanty po stronie serwera, które są uruchamiane wewnątrz strona składników web part: są blokami konstrukcyjnymi stron, które pojawiają się w witrynie programu SharePoint. Zobacz [bloków konstrukcyjnych: Składniki Web Part](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 Można tworzyć i debugować części sieci web w witrynie programu SharePoint przy użyciu szablonów z Visual Studio.  
  
## <a name="create-a-web-part-in-visual-studio"></a>Tworzenie składnika web part w programie Visual Studio
 Tworzenie składnika web part, dodając **składnika Web Part** element do każdego projektu programu SharePoint. Możesz użyć **składnika Web Part** elementu w rozwiązania w trybie piaskownicy lub farmy.  
  
 Jeśli chcesz wizualnie zaprojektować składnik web part za pomocą projektanta, Utwórz **wizualny składnik Web Part** projektu lub dodać **wizualny składnik Web Part** element do każdego projektu programu SharePoint. Możesz użyć **wizualny składnik Web Part** elementów w rozwiązaniu farmy.  
  
### <a name="web-part-item"></a>Element składnika Web part
 A **składnika Web Part** element zawiera pliki, które można użyć, aby zaprojektować składnik web part witryny programu SharePoint. Po dodaniu **składnika Web Part** elementu programu Visual Studio tworzy folder w projekcie, a następnie dodaje kilka plików do folderu. W poniższej tabeli opisano każdy plik.  
  
|Plik|Opis|  
|----------|-----------------|  
|*Elements.xml*|Zawiera informacje, których używa plik definicji funkcji w projekcie, aby wdrożyć składnik web part.|  
|plik .webpart|Udostępnia informacje wymagające wyświetlił składnik web part w galerii składników web part programu SharePoint.|  
|Plik kodu|Zawiera metody, które dodają formanty do składnika web part i które generują niestandardową zawartość wewnątrz składnika web part.|  
  
 Aby uzyskać więcej informacji, zobacz [jak: Tworzenie składnika web part programu SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### <a name="visual-web-part-item"></a>Element składnika programu Visual web part
 Program visual web part jest składnikiem web part, utworzonym przy użyciu projektanta Visual Web Developer w programie Visual Studio. Program visual web part działa tak samo, jak inny składnikk web part. Aby dodać formanty, takie jak przyciski i pola tekstowe do składnika web part, Dodaj kod do pliku XML. Jednak dodać formanty do wizualnego składnika web part, przeciągając je lub kopiując do składnika web part programu Visual Studio **przybornika**. Projektant następnie generuje kod wymagany w pliku XML. Zobacz [jak: Tworzenie części sieciowej SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## <a name="sharepoint-controls"></a>Formanty programu SharePoint
 Program Visual Studio zapewnia kilka formantów do tworzenia witryn SharePoint, takich jak strony aplikacji. Te kontrolki wyświetlają się w **przybornika** w obszarze **kontrolkami SharePoint**. Funkcja dla tych formantów wywodzi się z [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) przestrzeń nazw, która zawiera formanty serwera ASP.NET, które są używane na stronach witryny i listy programu SharePoint.  
  
|Nazwa kontrolki|Opis|  
|------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Wstawia ASP menu. Aby uzyskać więcej informacji, zobacz [omówienie Menu formantów](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Wstawia **łącze** elementu do *.aspx* strony i stosuje jeden lub więcej zewnętrznych arkuszy stylów zdefiniowanych przez **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Wstawia formant typu DataGodzina do *.aspx* strony.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Wstawia walidację bezpieczeństwa do *.aspx* strony|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Zwraca właściwość określonej listy.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Zwraca właściwość globalną bieżącej witryny sieci Web.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Wstaw łącze czytnika kanałów RSS do *.aspx* strony.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Udostępnia właściwości i metody rejestracji zasobów, takich jak skrypty na stronie, dzięki czemu można ich żądać Po wyrenderowaniu strony.|  
|[Motyw](http://go.microsoft.com/fwlink/?LinkId=235314)|Stosuje motyw do *.aspx* strony.|  
  
## <a name="debug-a-web-part"></a>Debugowanie składnika web part
 Można debugować projekt SharePoint, który zawiera składnik web part, tak samo, jak debuguje się inne projekty Visual Studio. Po uruchomieniu debugera programu Visual Studio, Visual Studio otwiera witrynę programu SharePoint.  
  
 Aby zacząć debugować kod, należy dodać składnik web part do strony składników web part w programie SharePoint.  
  
 Aby uzyskać więcej informacji na temat debugowania projektów programu SharePoint, zobacz [rozwiązań SharePoint Rozwiązywanie problemów z](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="visual-web-part-limitations"></a>Wizualnego składnika web part ograniczenia
 Począwszy od programu Visual Studio, można dodać wizualne części sieci web do rozwiązania programu SharePoint w trybie piaskownicy oraz rozwiązaniami farmy. Jednak wizualne składniki WebPart mają następujące ograniczenia:  
  
- Wizualne części sieci web nie obsługują zastępowalnych parametrów. Aby uzyskać więcej informacji, zobacz [parametrów zastępowalnych](../sharepoint/replaceable-parameters.md).  
  
- Formanty użytkownika lub wizualne części sieci web nie można przeciągnąć i porzucone lub kopiowane na wizualne części sieci web. Ta akcja powoduje błąd kompilacji.  
  
- Wizualne części sieci web nie obsługują bezpośrednio tokenów serwera SharePoint takich jak $SPUrl. Aby uzyskać więcej informacji, zobacz "Token ograniczeń w trybie piaskownicy wizualnego składnika Web Part" w temacie [rozwiązań SharePoint Rozwiązywanie problemów z](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
- Wizualne części sieci web w rozwiązania w trybie piaskownicy czasami wywołują błąd, "żądanie wykonania kodu w trybie piaskownicy zostało odrzucone, ponieważ usługi hosta kodu w trybie piaskownicy był zbyt zajęty, aby obsłużyć żądania." Aby uzyskać więcej informacji na temat tego błędu, zobacz ten wpis w [blogu zespołu deweloperskiego SharePoint](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
- Debugowanie kodu JavaScript po stronie serwera nie jest obsługiwana w programie Visual Studio, ale debugowanie kodu JavaScript po stronie klienta jest obsługiwane.  
  
   Chociaż możesz dodać liniowy JavaScript do pliku znaczników po stronie serwera, debugowanie nie jest obsługiwane dla punktów przerwania dodanych do tych znaczników. Aby debugować JavaScript, odwołania do zewnętrznego pliku JavaScript w pliku znacznikowania, a następnie ustaw punkty przerwania w pliku JavaScript.  
  
- Debugowanie inline [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] kod musi odbywać się w pliku wygenerowanego kodu, zamiast w pliku znaczników.  
  
- Wizualne części sieci web nie obsługują użycia `<@ Assembly Src=` dyrektywy.  
  
- Formanty i niektóre sieci web programu SharePoint [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] formanty nie są obsługiwane w trybie piaskownicy środowiska programu SharePoint. Jeśli używane są nieobsługiwane regulatory na wizualnego składnika web part w rozwiązania w trybie piaskownicy, błąd, pojawi się "Nazwy typu lub przestrzeni nazw"Motyw"nie istnieje w przestrzeni nazwy"Microsoft.SharePoint.WebControls"".  
  
  Aby uzyskać więcej informacji dotyczących rozwiązań sandbox, zobacz [różnicach w trybie piaskownicy oraz rozwiązaniami farmy](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="create-older-style-sharepoint-based-web-parts"></a>Tworzenie opartych na programie SharePoint web Part na starszym stylu
 Można użyć szablonów w programie Visual Studio do tworzenia niestandardowych [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] składniki web Part programu SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] części sieci Web są tworzone w górnej części [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] infrastrukturze części sieci web i są polecane dla nowych projektów.  
  
 W bardzo nielicznych przypadkach być może trzeba utworzyć składnik web part przy użyciu starszego stylu składnika opartych na programie SharePoint web part. Używasz programu Visual Studio do tworzenia tego typu części sieci web, ale Visual Studio nie zapewnia żadnych szablonów, które są przeznaczone specjalnie do pomocy w ich tworzeniu.  
  
 Aby uzyskać więcej informacji na temat Kiedy warto utworzyć oparty na programie SharePoint składnik web part na starszym stylu zobacz [infrastruktura składnika WebPart w Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290). Aby uzyskać więcej informacji o sposobie tworzenia składnika web part przy użyciu starszego stylu składnika opartych na programie SharePoint web part, zobacz [Instruktaż tworzenia podstawowego składnika Web Part programu SharePoint](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## <a name="related-topics"></a>Tematy pokrewne
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Tworzenie składnika web part programu SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Dowiesz się, jak utworzyć składniki web Part dla stron programu SharePoint.|  
|[Instrukcje: Tworzenie części sieciowej SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Dowiesz się, jak utworzyć składniki web Part programu SharePoint przy użyciu powierzchni projektowej.|  
|[Instrukcje: Tworzenie kontrolki użytkownika dla części strony lub sieci web aplikacji programu SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Dowiesz się, jak utworzyć niestandardowe formanty wielokrotnego użytku, które mogą być wykorzystane przez strony aplikacji i składników web Part, które są uruchamiane w programie SharePoint.|  
|[Przewodnik: Tworzenie składnika web part programu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Opisuje sposób projektowania składnika web part programu SharePoint.|  
|[Przewodnik: Tworzenie składnika web part programu SharePoint przy użyciu narzędzia Projektant](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Opisuje sposób projektowania składnika web part programu SharePoint, przeciągając formanty do powierzchni projektowej.|  
|[Przewodnik: Tworzenie składnika web part Silverlight, który wyświetlającego dane OData dla programu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Opisuje sposób projektowania składnika web part programu SharePoint, który obsługuje aplikację Silverlight i wyświetla dane z list programu SharePoint.|  

---
title: Tworzenie składniki Web Part dla programu SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: 4824c358f81f2cf757f037611ed70ba9b8935130
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740160"
---
# <a name="create-web-parts-for-sharepoint"></a>Tworzenie składników Web Part dla programu SharePoint
  Za pomocą części sieci Web, można modyfikować zawartość, wygląd i zachowanie stron witryny programu SharePoint za pomocą przeglądarki. Części sieci Web to kontrolki po stronie serwera, które są uruchamiane wewnątrz strony składnika Web Part: są to bloki konstrukcyjne stron, które są wyświetlane w witrynie programu SharePoint. Zobacz [blok konstrukcyjny: składniki Web Part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

 Możesz tworzyć i debugować części sieci Web w witrynie programu SharePoint przy użyciu szablonów z programu Visual Studio.

## <a name="create-a-web-part-in-visual-studio"></a>Tworzenie składnika Web Part w programie Visual Studio
 Utwórz składnik Web Part, dodając element **składnika Web Part** do dowolnego projektu programu SharePoint. Można użyć elementu **składnika Web Part** w rozwiązaniu w trybie piaskownicy lub w rozwiązaniu farmy.

 Jeśli chcesz zaprojektować składnik Web Part wizualnie przy użyciu projektanta, Utwórz projekt **Visual Web Part** lub Dodaj element **wizualny składnik Web Part** do dowolnego projektu programu SharePoint. Elementu **Visual Web Part** można użyć tylko w ramach rozwiązania farmy.

### <a name="web-part-item"></a>Element składnika Web Part
 Element **składnika Web Part** zawiera pliki, których można użyć do projektowania składnika Web Part dla witryny programu SharePoint. Po dodaniu elementu **składnika Web Part** program Visual Studio tworzy folder w projekcie, a następnie dodaje kilka plików do tego folderu. W poniższej tabeli opisano każdy plik.

|Plik|Opis|
|----------|-----------------|
|*Elements.xml*|Zawiera informacje, które są używane przez plik definicji funkcji w projekcie do wdrażania składnika Web Part.|
|plik WebPart|Zawiera informacje o tym, że program SharePoint musi wyświetlić składnik Web Part w galerii składników Web Part.|
|Plik kodu|Zawiera metody, które dodają formanty do składnika Web Part i generują zawartość niestandardową w składniku Web Part.|

 Aby uzyskać więcej informacji, zobacz [How to: Create a SharePoint Web Part](../sharepoint/how-to-create-a-sharepoint-web-part.md).

### <a name="visual-web-part-item"></a>Element wizualnego składnika Web Part
 Wizualny składnik Web Part to składnik Web Part tworzony przy użyciu projektanta Visual Web Developer w programie Visual Studio. Wizualny składnik Web Part działa tak samo jak każdy inny składnik Web Part. Aby dodać kontrolki, takie jak przyciski i pola tekstowe, do składnika Web Part, należy dodać kod do pliku XML. Można jednak dodać kontrolki do wizualnego składnika Web Part, przeciągając je lub kopiując do składnika Web Part z **przybornika**programu Visual Studio. Następnie Projektant generuje wymagany kod w pliku XML. Zobacz [jak: Tworzenie składnika Web Part programu SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

## <a name="sharepoint-controls"></a>Kontrolki programu SharePoint
 Program Visual Studio udostępnia pewne kontrolki służące do tworzenia stron programu SharePoint, takich jak strony aplikacji. Te kontrolki są wyświetlane w **przyborniku** w obszarze **kontrolki programu SharePoint**. Funkcje tych formantów pochodzą z przestrzeni nazw [Microsoft. SharePoint. WebControls](/previous-versions/office/sharepoint-server/ms413880(v=office.15)) , która zawiera kontrolki serwera ASP.NET, które są używane na stronach witryny i listy programu SharePoint.

|Nazwa kontrolki|Opis|
|------------------|-----------------|
|[AspMenu](/previous-versions/office/sharepoint-server/ms454108(v=office.15))|Wstawia menu ASP. Aby uzyskać więcej informacji, zobacz temat [formant menu — Omówienie](/previous-versions/ecs0x9w5(v=vs.140)).|
|[CssLink](/previous-versions/office/sharepoint-server/ms439048(v=office.15))|Wstawia element **link** do strony *. aspx* i stosuje co najmniej jeden zewnętrzny arkusz stylów zdefiniowany przez **CssRegistration**.|
|[DateTimeControl](/previous-versions/office/sharepoint-server/ms414993(v=office.15))|Wstawia kontrolkę DateTime do strony *. aspx* .|
|[FormDigest](/previous-versions/office/sharepoint-server/ms416616(v=office.15))|Wstawia walidację zabezpieczeń do strony *. aspx*|
|[SELECT](/previous-versions/office/sharepoint-server/ms455032(v=office.15))|Zwraca właściwość określonej listy.|
|[ProjectProperty](/previous-versions/office/sharepoint-server/ms478990(v=office.15))|Zwraca właściwość globalną bieżącej witryny sieci Web.|
|[RssLink](/previous-versions/office/sharepoint-server/ms457574(v=office.15))|Wstawia link do źródła danych RSS do strony *. aspx* .|
|[ScriptLink](/previous-versions/office/sharepoint-server/ms411959(v=office.15))|Udostępnia właściwości i metody rejestrowania zasobów, takich jak skrypty, na stronie, aby można było żądać ich podczas renderowania strony.|
|[Motyw](/previous-versions/office/sharepoint-server/ms460735(v=office.15))|Stosuje motyw do strony *. aspx* .|

## <a name="debug-a-web-part"></a>Debugowanie składnika Web Part
 Można debugować projekt programu SharePoint, który zawiera składnik Web Part tak samo jak debugowanie innych projektów programu Visual Studio. Po uruchomieniu debugera programu Visual Studio program Visual Studio otwiera witrynę programu SharePoint.

 Aby rozpocząć debugowanie kodu, Dodaj składnik Web Part do strony składnika Web Part w programie SharePoint.

 Aby uzyskać więcej informacji na temat debugowania projektów programu SharePoint, zobacz [Rozwiązywanie problemów z rozwiązaniami programu SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="visual-web-part-limitations"></a>Ograniczenia wizualnego składnika Web Part
 Począwszy od programu Visual Studio, można dodawać wizualne składniki Web Part do rozwiązań programu SharePoint w trybie piaskownicy oraz rozwiązań farmy. Jednak wizualne części sieci Web mają następujące ograniczenia:

- Wizualne składniki Web Part nie obsługują wymiennych parametrów. Aby uzyskać więcej informacji, zobacz [Parametry wymienne](../sharepoint/replaceable-parameters.md).

- Kontrolki użytkownika lub wizualne części sieci Web nie mogą być przeciągane i upuszczane ani kopiowane na wizualne części sieci Web. Ta akcja powoduje błąd kompilacji.

- Wizualne składniki Web Part nie obsługują bezpośrednio tokenów serwera programu SharePoint, takich jak $SPUrl. Aby uzyskać więcej informacji, zobacz "ograniczenia tokenu w składniki Web Part wizualizacji w trybie piaskownicy" w temacie [Rozwiązywanie problemów z rozwiązaniami programu SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

- Wizualne części sieci Web w rozwiązaniu w trybie piaskownicy czasami pobierają błąd "żądanie wykonania kodu w trybie piaskownicy zostało odrzucone, ponieważ usługa hosta kodu w trybie piaskownicy była zbyt zajęta, aby obsłużyć żądanie". Aby uzyskać więcej informacji na temat tego błędu, zobacz ten wpis w [blogu zespołu deweloperów programu SharePoint](/archive/blogs/sharepointdev/error-the-sandboxed-code-execution-request-was-refused-because-the-sandboxed-code-host-service-was-too-busy-to-handle-the-request-ricky-kirkham#10149157).

- Debugowanie kodu JavaScript po stronie serwera nie jest obsługiwane w programie Visual Studio, ale Debugowanie kodu JavaScript po stronie klienta jest obsługiwane.

   Chociaż można dodać wbudowany kod JavaScript do pliku znaczników po stronie serwera, debugowanie nie jest obsługiwane dla punktów przerwania dodanych do znacznika. Aby debugować JavaScript, odwołując się do zewnętrznego pliku JavaScript w pliku znaczników, a następnie ustaw punkty przerwania w pliku JavaScript.

- Debugowanie kodu śródwierszowego [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] należy wykonać w wygenerowanym pliku kodu, a nie w pliku znaczników.

- Wizualne składniki Web Part nie obsługują stosowania `<@ Assembly Src=` dyrektywy.

- Kontrolki sieci Web programu SharePoint i niektóre [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] kontrolki nie są obsługiwane w środowisku w trybie piaskownicy programu SharePoint. Jeśli formanty nieobsługiwane są używane w składniku Web Part w rozwiązaniu w trybie piaskownicy, zostanie wyświetlony komunikat o błędzie "typ lub nazwa przestrzeni nazw" motyw "nie istnieje w przestrzeni nazw" Microsoft. SharePoint. WebControls "".

  Aby uzyskać więcej informacji o rozwiązaniach w trybie piaskownicy, zobacz [różnice między rozwiązaniami w trybie piaskownicy a farmą](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="create-older-style-sharepoint-based-web-parts"></a>Tworzenie starszych składników Web Part opartych na programie SharePoint
 Za pomocą szablonów w programie Visual Studio można tworzyć niestandardowe [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] składniki Web Part dla programu SharePoint. [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] części sieci Web są zbudowane na podstawie [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] infrastruktury składnika Web Part i są zalecanym typem dla nowych projektów.

 W bardzo niewielkich przypadkach może być konieczne utworzenie składnika Web Part przy użyciu starszej części sieci Web opartej na programie SharePoint. Możesz użyć programu Visual Studio, aby utworzyć te typy części sieci Web, ale program Visual Studio nie udostępnia żadnych szablonów, które zostały zaprojektowane specjalnie w celu ułatwienia ich tworzenia.

 Aby uzyskać więcej informacji na temat sytuacji, w których można utworzyć starszy, oparty na programie SharePoint składnik Web Part, zobacz [infrastruktura części sieci Web w programie Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms415560(v=office.14)). Aby uzyskać więcej informacji na temat sposobu tworzenia składnika Web Part przy użyciu starszego dla programu SharePoint składnika sieci Web, zobacz [Przewodnik tworzenia podstawowej części sieci Web programu SharePoint](/previous-versions/office/ms452873(v=office.14)).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Instrukcje: Tworzenie składnika Web Part programu SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Pokazuje, w jaki sposób utworzyć składniki Web Part dla stron programu SharePoint.|
|[Instrukcje: Tworzenie składnika Web Part programu SharePoint przy użyciu narzędzia Projektant](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Pokazuje, w jaki sposób utworzyć składniki Web Part dla programu SharePoint przy użyciu powierzchni projektowej wizualnej.|
|[Instrukcje: Tworzenie kontrolki użytkownika dla strony aplikacji lub składnika sieci Web programu SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Pokazuje, jak utworzyć niestandardowe, wielokrotnego użytku kontrolki, które mogą być używane przez strony aplikacji i składniki Web Part, które są uruchamiane w programie SharePoint.|
|[Przewodnik: Tworzenie składnika Web Part dla programu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Opisuje sposób projektowania składnika Web Part dla programu SharePoint.|
|[Przewodnik: Tworzenie składnika Web Part dla programu SharePoint przy użyciu narzędzia Projektant](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Opisuje sposób projektowania składnika Web Part dla programu SharePoint przez przeciąganie formantów do powierzchni projektowej wizualnej.|
|[Przewodnik: Tworzenie składnika Web Part Silverlight, który wyświetla składnik OData dla programu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Opisuje sposób projektowania składnika Web Part programu SharePoint, który hostuje aplikację Silverlight i wyświetla dane z list programu SharePoint.|
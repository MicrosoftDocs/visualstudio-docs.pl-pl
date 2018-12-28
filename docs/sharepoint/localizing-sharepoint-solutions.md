---
title: Lokalizowanie rozwiązań SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3897efa937991b598f6aae1cf24781ab2ce26c37
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684746"
---
# <a name="localize-sharepoint-solutions"></a>Lokalizowanie rozwiązań SharePoint

  Proces przygotowywania aplikacji, dzięki czemu mogą być używane na całym świecie, jest nazywany lokalizacji. Lokalizacja jest tłumaczeniem zasobów do określonej kultury. Aby uzyskać więcej informacji, zobacz [Globalizing i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md). Ten temat zawiera omówienie sposobów lokalizacji rozwiązania SharePoint.  
  
 Aby zlokalizować rozwiązanie, Usuń niezmienne ciągi z kodu i wyciągnij je do plików zasobów. Plik zasobów jest [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-oparty na pliku z *resx* rozszerzenia. Plik źródłowy zawiera tłumaczone wersje ciągów wykorzystanych w Twoim rozwiązaniu. Aby uzyskać więcej informacji, zobacz [zasoby w aplikacjach](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Dodaj tylko zasoby ciągu do plików zasobów rozwiązanie programu SharePoint. Chociaż Edytor zasobów umożliwia dodawanie zasobów niebędących ciągami, zasoby bez ciągów nie są wdrażane do programu SharePoint.  
  
## <a name="resource-files"></a>Pliki zasobów
 Istnieją trzy rodzaje plików zasobów: domyślny, neutralny językowo i specyficznych dla języka.  
  
|Typ plików zasobów|Opis|  
|------------------------|-----------------|  
|Domyślny|Znany również jako bazoey zasoby, domyślne pliki zasobów zawierją ciągi zlokalizowane dla domyślnej kultury, na przykład w języku angielskim. Są one używane, jeśli można znaleźć nie zlokalizowane pliki zasobów dla określonego języka. Domyślne zasoby nie mają osobnych plików, są one przechowywane w zestawie aplikacji głównej.|  
|Niezależny od języka|Plik zasobów zawiera ciągi zlokalizowane dla języka, ale nie konkretną kulturę. Na przykład "fr", francuski.|  
|Specyficzne dla języka|Plik zasobów zawiera ciągi zlokalizowane dla języka i kultury. Na przykład "fr-CA" Francuski kanadyjski.|  
  
 Aby uzyskać więcej informacji, zobacz [hierarchiczna organizacja zasobów do lokalizacji](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Aby określić domyślne pliki zasobów w projektach SharePoint, które da się opracować na [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wybierz **niezmienny język (niezmienny Kraj)** na liście kultury **Dodaj zasób** okno dialogowe, gdy użytkownik Dodawanie pliku zasobu.  
  
## <a name="localize-visual-studio-sharepoint-solutions"></a>Lokalizowanie rozwiązań programu Visual Studio SharePoint
 Podczas lokalizacji rozwiązania, należy rozważyć wszystkie informacje tekstowe, które Twoje rozwiązania Wyświetla użytkownikom. Komunikaty informacyjne, komunikaty o błędach i [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] parametry muszą być przetłumaczone i te tłumaczenia są umieszczane w plikach zasobów.  
  
 Każdy ciąg w pliku zasobów ma unikatowy identyfikator. Użyj tego samego identyfikatora dla przetłumaczonego ciągu w każdym pliku zasobów. Na przykład jeśli "Ciąg1" jest identyfikatorem pierwszego ciągu w domyślnym pliku zasobów, należy użyć tego samego identyfikatora dla pierwszego ciągu w plikach zasobów specyficznych dla języka.  
  
 Istnieją trzy obszary typowo lokalizowane w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikacji programu SharePoint: funkcje, znacznikowanie strony i kod. Dla celów ilustracyjnych następujące sekcje zakładają, że masz rozwiązanie SharePoint, które chcesz przetłumaczyć na język niemiecki i japoński. Domyślnym językiem jest angielski.  
  
### <a name="localize-features"></a>Lokalizowanie funkcji
 Aby zlokalizować funkcję, musisz zastąpić niezmienny tytuł i opis funkcji z wyrażeniem, które odwołuje się do przetłumaczonego tytułu i ciągu w zlokalizowanym pliku zasobów. Wprowadzenie tej zmiany w **projektanta funkcji** w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Lokalizowanie funkcji](../sharepoint/how-to-localize-a-feature.md).  
  
 Aby zlokalizować swoje funkcje angielskiego na niemiecki i japoński, Dodaj trzy elementy projektu pliku zasobów do projektu: jeden dla angielskiego, jeden dla niemieckiego i jeden dla japońskiego. Plików zasobów funkcji nie można użyć do zlokalizowania znaczników ASPX lub kodu. wymagane są oddzielne pliki zasobów.  
  
 Po utworzeniu funkcji plików zasobów, należy dodać do nich przetłumaczone ciągi. Dostęp do zlokalizowanych ciągów z wyrażeniem w następującym formacie:  
  
```aspx-csharp  
$Resources:String ID  
```  
  
 Zasoby funkcji w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zawsze mają nazwę zasoby. Wybranie języka niż język niezmienny, następnie kultury [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] jest dodawany do nazwy pliku zasobów. Na przykład jeśli dodasz plik zasobów funkcji niezmienny język (ustawienie domyślne), jest to *Resources.resx*. Jeśli dodasz zasobu funkcji specyficznych dla języka wybierając kulturę japońską (Japonia), plik nosi *nazwę Resources.ja-JP.resx*. Nazwy pliku zasobów funkcji są automatycznie przypisywane i nie można jej zmienić.  
  
 Zakres zasobów funkcji jest lokalny dla funkcji, które są dodawane do. Aby utworzyć zasoby, które mogą być używane przez wszystkie funkcję lub plik elementów w rozwiązaniu, Dodaj **plik zasobów globalnych** elementu projektu zamiast pliku zasobu funkcji. **Plik zasobów globalnych** elementu projektu znajduje się w **2010** folderze **SharePoint** w **Dodaj nowy element** okno dialogowe. Wdrażanie globalnych plików zasobów do folderu \Resources w folderze głównym programu SharePoint.  
  
### <a name="localize-aspx-page-markup"></a>Lokalizowanie znaczniki strony ASPX
 Aby zlokalizować [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stron, Dodaj trzy elementy projektu pliku zasobów do projektu: jeden dla angielskiego, jeden dla niemieckiego i jeden dla japońskiego. Jeśli nie masz do lokalizowania kodu oprócz znaczników, zamiast tego można dodać pliki zasobów globalnych.  
  
 Podaj nazwę plikowi zasobów języka domyślnego. Nadaj zlokalizowanym plikom zasobów taką samą nazwę, z kulturą specyficzną dla języka dołączoną [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Na przykład *MyAppResources.de-DE.resx* dla języka niemieckiego i *MyAppResources.ja-JP.resx* dla języka japońskiego.  
  
 Ustaw **typu wdrożenia** właściwości każdego pliku zasobu na **AppGlobalResource**. To powoduje, że pliki zasobów wdrożyć do folderu App_GlobalResources, gdzie są dostępne dla wszystkich stron ASPX i kontrolek w rozwiązaniu. App_GlobalResources folder znajduje się w C:\inetpub\wwwroot\wss\VirtualDirectories\\< numer portu\>\App_GlobalResources.  
  
> [!NOTE]  
>  Jeśli używasz plików zasobów nieglobalnych, przenieś je do folderu elementu projektu, aby włączyć właściwość wdrożenia i inne właściwości specyficzne dla programu SharePoint.  
  
 Pliki zasobów znaczników ASPX może również służyć do zlokalizowania kodu. Jeśli używasz zasobów do lokalizowania kodu Oprócz oznakowania aspx, pozostaw ustawienie właściwości Akcja kompilacji każdego pliku jako zasób osadzony, aby spowodować, że zasób można skompilować do zestawu satelickiego. Jednak jeśli używasz plików zasobów tylko do zlokalizowania znaczników, opcjonalnie można zmienić akcji kompilacji do zawartości, aby uniemożliwić pliku są kompilowane do zestawu głównej aplikacji.  
  
 Zastąp wszystkie ciągi właściwość zakodowane sprzętowo w znaczników stron i formantów ASPX wyrażeniem w następującym formacie:  
  
```aspx-csharp  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Na przykład:  
  
```aspx-csharp  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Dla tekstu ASPX należy użyć wyrażenia w następującym formacie:  
  
```aspx-csharp  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Na przykład:  
  
```aspx-csharp  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Aby uzyskać więcej informacji, zobacz [jak: Lokalizowanie znacznika ASPX](../sharepoint/how-to-localize-aspx-markup.md).  
  
### <a name="localize-code"></a>Lokalizowanie kodu
 Oprócz lokalizowania ciągów funkcji i [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] znaczników, musisz również zlokalizować ciągi komunikatów i ciągi błędów, które pojawiają się w kodzie rozwiązania. Zlokalizowane informacyjne i komunikaty o błędach są zawarte w zestawach satelickich. Zestawy satelickie zawierają ciągi, które są widoczne dla użytkowników, takie jak [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] wiadomości tekstowe i dane wyjściowe jak wyjątki.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] używa standardowego modelu topologi gwiaździstej .NET Framework. Koncentrator lub zestaw programu głównego zawiera zasoby domyślnego języka. Szprychy lub zestawy satelickie zawierają zasoby specyficzne dla języka. Aby uzyskać więcej informacji, zobacz [Packaging and Deploying Resources](http://go.microsoft.com/fwlink/?LinkId=179280). Zestawy satelickie są skompilowane z zasobu (*resx*) plików. Podczas dodawania plików zasobów specyficznych dla języka projektu i pakietu rozwiązań [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kompiluje pliki zasobów w zestawy satelit nazwane *.resources.dll {Nazwa projektu}*.  
  
 Podobnie jak w przypadku znaczników ASPX zlokalizowania kodu aplikacji programu SharePoint, dodając osobne lementy projektu pliku zasobów do projektu. jeden dla języka domyślnego i jeden dla każdego zlokalizowanego języka. Jednakże jak wspomniano wcześniej, jeśli masz już pliki zasobów do lokalizowania znaczników ASPX, możesz ponownie użyć ich do lokalizacji kodu. Jeśli musisz utworzyć pliki zasobów, nadaj plikowi zasobów języka domyślnego nazwę wybranego z dołączonym *resx* rozszerzenia. Nazwij zlokalizowane pliki zasobów taką samą nazwę z kulturą specyficzną dla języka dołączoną [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Ustaw właściwość akcji kompilacji każdego pliku zasobu na zasób osadzony, aby włączyć funkcję tworzenia zestawów zasobów satelickich.  
  
 Aby utworzyć zbiór satelit, skompiluj projekt, a następnie dodaj pliki jako dodatkowe zestawy za pomocą **zaawansowane** karcie **projektancie pakietu**. Podczas dodawania zestawów, należy poprzedzić kultury [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] folder do ścieżki lokalizacji, takich jak *de-DE\\.resources.dll {nazwy elementu projektu}*. Dzięki temu pakiet, który ma zawierać pliki, które mają taką samą nazwę.  
  
 W kodzie, Zastąp zakodowane sprzętowo ciągi połączeń w celu <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metody przy użyciu następującej składni:  
  
```aspx-csharp  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Aby uzyskać więcej informacji, zobacz [jak: Lokalizowanie kodu](../sharepoint/how-to-localize-code.md).  
  
#### <a name="web-part-code-localization"></a>Lokalizacja kodu części sieci Web
 Części sieci Web obejmują funkcję edytora właściwości niestandardowej, która zawiera atrybuty kodu wykorzystujące ciągi niezmienne, takie jak WebDisplayName, Category i WebDescription. Aby zastąpić wartości ciągu tymi atrybutami, Utwórz osobna klasę, która jest pochodną klasy atrybutu. W tych klasach ustaw właściwość atrybutu. Właściwość atrybutu zależy od klasy bazowej. Na przykład właściwość atrybutu WebDisplayName to DisplayNameValue, a właściwość atrybutu WebDescription to DescriptionValue.  
  
 W klasie pochodnej odwoływać się do Identyfikatora ciągu z pliku zasobów i obiektu ResourceManager, aby uzyskać wartość zlokalizowaną dla identyfikatora ciągu. Zwróć tę wartość do atrybutu edytora właściwości.  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Lokalizowanie funkcji](../sharepoint/how-to-localize-a-feature.md)   
 [Instrukcje: Lokalizowanie znacznika ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Instrukcje: Lokalizowanie kodu](../sharepoint/how-to-localize-code.md)   
 [Instrukcje: Dodawanie pliku zasobu](../sharepoint/how-to-add-a-resource-file.md)   
 [Instrukcje: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości oraz uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  

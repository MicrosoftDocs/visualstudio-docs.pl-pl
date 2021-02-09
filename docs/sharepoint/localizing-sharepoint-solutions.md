---
title: Lokalizowanie rozwiązań SharePoint | Microsoft Docs
description: Lokalizowanie rozwiązań SharePoint przez usunięcie zakodowanych ciągów z kodu i ich abstrakcję do plików zasobów opartych na języku XML (. resx) zawierających przetłumaczone ciągi.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a216e57bc9da15fca625e71c7e0430d4fbf4164b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873557"
---
# <a name="localize-sharepoint-solutions"></a>Lokalizowanie rozwiązań SharePoint

  Proces przygotowywania aplikacji w taki sposób, aby mogły być używane na całym świecie, jest znany jako lokalizacja. Lokalizacja tłumaczy zasoby na określoną kulturę. Aby uzyskać więcej informacji, zobacz [globalizacja i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md). Ten temat zawiera omówienie sposobu lokalizowania rozwiązania programu SharePoint.

 Aby zlokalizować rozwiązanie, Usuń zakodowane ciągi z kodu i podziel je na pliki zasobów. Plik zasobów jest [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] plikiem opartym na rozszerzeniu *resx* . Plik zasobów zawiera przetłumaczone wersje ciągów używanych w rozwiązaniu. Aby uzyskać więcej informacji, zobacz [zasoby w aplikacjach](/previous-versions/dotnet/netframework-4.0/f45fce5x(v=vs.100)).

> [!NOTE]
> Dodaj tylko zasoby ciągu do plików zasobów rozwiązania programu SharePoint. Mimo że edytor zasobów pozwala dodawać zasoby niebędące ciągami, nie należy wdrażać zasobów niebędących ciągami w programie SharePoint.

## <a name="resource-files"></a>Pliki zasobów
 Istnieją trzy rodzaje plików zasobów: domyślne, niezależne od języka i specyficzne dla języka.

|Typ pliku zasobu|Opis|
|------------------------|-----------------|
|Domyślne|Znany również jako zasób rezerwowy, domyślne pliki zasobów zawierają ciągi zlokalizowane dla kultury domyślnej, takie jak angielski. Są one używane, jeśli nie można znaleźć zlokalizowanych plików zasobów dla określonego języka. Zasoby domyślne nie mają oddzielnych plików, są one przechowywane w głównym zestawie aplikacji.|
|Niezależny od języka|Plik zasobów zawierający ciągi zlokalizowane dla języka, ale nie do określonej kultury. Na przykład "fr" dla języka francuskiego.|
|Specyficzne dla języka|Plik zasobów zawierający ciągi zlokalizowane dla języka i kultury. Na przykład "fr-CA" dla francuskiego Kanady.|

 Aby uzyskać więcej informacji, zobacz [hierarchiczna organizacja zasobów do lokalizacji](../ide/globalizing-and-localizing-applications.md).

 Aby określić domyślne pliki zasobów w projektach programu SharePoint, które są opracowywane w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , wybierz pozycję **niezmienny język (kraj** niebędący) na liście kultura okna dialogowego **Dodawanie zasobu** , gdy zostanie dodany plik zasobów.

## <a name="localize-visual-studio-sharepoint-solutions"></a>Lokalizowanie rozwiązań programu Visual Studio SharePoint
 Podczas lokalizowania rozwiązania należy wziąć pod uwagę wszystkie informacje tekstowe, które są wyświetlane dla danego rozwiązania użytkownikom. Komunikaty informacyjne, komunikaty o błędach i [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] ciągi muszą być tłumaczone i te tłumaczenia są umieszczane w plikach zasobów.

 Każdy ciąg w pliku zasobów ma unikatowy identyfikator. Użyj tego samego identyfikatora dla przetłumaczonego ciągu w każdym pliku zasobów. Na przykład, jeśli "ciąg1" jest identyfikatorem pierwszego ciągu w domyślnym pliku zasobów, użyj tego samego identyfikatora dla pierwszego ciągu w plikach zasobów specyficznych dla języka.

 Istnieją trzy obszary, które są zwykle lokalizowane w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aplikacjach SharePoint: funkcje, znaczniki strony aspx i kod. Na potrzeby ilustracji w poniższych sekcjach założono, że masz rozwiązanie SharePoint, które chcesz zlokalizować w języku niemieckim i japońskim. Językiem domyślnym jest język angielski.

### <a name="localize-features"></a>Lokalizowanie funkcji
 Aby zlokalizować funkcję, należy zamienić trwale zakodowany tytuł i opis funkcji na wyrażenie odwołujące się do przetłumaczonego tytułu i ciągu w zlokalizowanym pliku zasobów. Ta zmiana została wprowadzona w **Projektancie funkcji** w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [How to: lokalizuje funkcję](../sharepoint/how-to-localize-a-feature.md).

 Aby zlokalizować funkcję w języku angielskim w językach niemieckim i japońskim, Dodaj trzy elementy projektu pliku zasobów do projektu: jeden dla języka angielskiego, jeden dla języka niemieckiego i jeden dla języka japońskiego. Plików zasobów funkcji nie można używać do lokalizowania znaczników ASPX ani kodu; dla nich wymagane są osobne pliki zasobów.

 Po utworzeniu plików zasobów funkcji należy dodać do nich przetłumaczone ciągi. Uzyskaj dostęp do zlokalizowanych ciągów z wyrażeniem w następującym formacie:

```aspx-csharp
$Resources:String ID
```

 Zasoby funkcji w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] są zawsze nazwanymi zasobami. W przypadku wybrania języka innego niż Język niezmienny, [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] do nazwy pliku zasobu zostanie dodana kultura. Na przykład, jeśli dodasz plik zasobów funkcji o niezmiennym języku (default), jest on nazywany *resources. resx*. Jeśli dodasz zasób funkcji specyficzny dla języka, wybierając kulturę języka japońskiego (Japonia), plik ma nazwę *resources. ja-JP. resx*. Nazwy plików zasobów funkcji są automatycznie przypisywane i nie można ich zmienić.

 Zakres zasobów funkcji jest lokalny dla funkcji, do której są dodawane. Aby utworzyć zasoby, które mogą być używane przez dowolny plik funkcji lub elementu w rozwiązaniu, Dodaj element projektu **plik zasobów globalnych** zamiast pliku zasobów funkcji. Element projektu **plik zasobów globalnych** znajduje się w folderze **2010** w obszarze **SharePoint** w oknie dialogowym **Dodaj nowy element** . Pliki zasobów globalnych są wdrażane w folderze \Resources folderu głównego programu SharePoint.

### <a name="localize-aspx-page-markup"></a>Lokalizowanie znaczników strony ASPX
 Aby zlokalizować [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] strony, Dodaj trzy elementy projektu pliku zasobów do projektu: jeden dla języka angielskiego, jeden dla języka niemieckiego i jeden dla języka japońskiego. Jeśli nie trzeba lokalizować kodu oprócz znaczników, zamiast tego można dodać pliki zasobów globalnych.

 Podaj nazwę domyślnego pliku zasobów języka. Nadaj zlokalizowanym plikom zasobów taką samą nazwę dołączoną do kultury specyficznej dla języka [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Na przykład *MyAppResources.de-de. resx* dla języka niemieckiego i *MyAppResources. ja-JP. resx* dla języka japońskiego.

 Ustaw właściwość **typ wdrożenia** każdego pliku zasobów na **AppGlobalResource**. Powoduje to, że pliki zasobów zostaną wdrożone w folderze App_GlobalResources, gdzie są dostępne dla wszystkich stron ASPX i kontrolek w rozwiązaniu. Folder App_GlobalResources znajduje się w folderze C:\inetpub\wwwroot\wss\VirtualDirectories \\<numer portu \> \ App_GlobalResources.

> [!NOTE]
> Jeśli używasz plików zasobów nieglobalnych, przenieś je do folderu elementów projektu, aby włączyć właściwość typu wdrożenia i inne właściwości specyficzne dla programu SharePoint.

 Pliki zasobów znaczników ASPX mogą również służyć do lokalizowania kodu. Jeśli używasz zasobów do lokalizowania kodu oprócz znacznika ASPX, pozostaw ustawienie właściwości Akcja kompilacji każdego pliku jako zasób osadzony, aby spowodować skompilowanie zasobu w zestawie satelickim. Jeśli jednak używasz plików zasobów tylko do lokalizowania znaczników, możesz opcjonalnie zmienić akcję kompilacji na zawartość, aby zapobiec skompilowaniu pliku w głównym zestawie aplikacji.

 Zamień wszystkie zakodowane ciągi właściwości na stronach ASPX i kontroluje znaczniki przy użyciu wyrażenia w następującym formacie:

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Na przykład:

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 Dla ASPX jako tekst Użyj wyrażenia w następującym formacie:

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Na przykład:

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 Aby uzyskać więcej informacji, zobacz [How to: lokalizuje znaczniki aspx](../sharepoint/how-to-localize-aspx-markup.md).

### <a name="localize-code"></a>Lokalizowanie kodu
 Oprócz lokalizowania ciągów i znaczników funkcji należy [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] również lokalizować ciągi komunikatów i ciągi błędów, które pojawiają się w kodzie rozwiązania. Zlokalizowane informacje informacyjne i komunikaty o błędach są zawarte w zestawach satelickich. Zestawy satelickie zawierają ciągi, które są widoczne dla użytkowników, takie jak [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] komunikaty tekstowe i wyjściowe, takie jak wyjątki.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] używa standardowego modelu .NET Framework Hub i szprych. Koncentrator lub zestaw programu głównego zawiera zasoby języka domyślnego. Szprychy lub zestawy satelickie zawierają zasoby specyficzne dla języka. Aby uzyskać więcej informacji, zobacz [pakowanie i wdrażanie zasobów](/previous-versions/dotnet/netframework-4.0/sb6a8618(v=vs.100)). Zestawy satelickie są kompilowane z plików zasobów (*. resx*). Po dodaniu plików zasobów specyficznych dla języka do projektu i pakietu rozwiązania program [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kompiluje pliki zasobów do zestawów satelickich o nazwie *{Project Name} .resources.dll*.

 Podobnie jak w przypadku znaczników ASPX, można zlokalizować kod aplikacji programu SharePoint, dodając oddzielne elementy projektu pliku zasobów do projektu; jeden dla języka domyślnego i jeden dla każdego zlokalizowanego języka. Jednak jak wspomniano wcześniej, jeśli masz już pliki zasobów do lokalizowania znaczników ASPX, można użyć ich ponownie w celu zlokalizowania kodu. Jeśli musisz utworzyć pliki zasobów, Nadaj plikowi zasobów języka domyślnego nazwę dołączoną z rozszerzeniem *resx* . Nazwij zlokalizowane pliki zasobów o tej samej nazwie dołączonej do kultury specyficznej dla języka [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Ustaw właściwość Akcja kompilacji każdego pliku zasobów na zasób osadzony, aby umożliwić tworzenie zestawów zasobów satelity.

 Aby utworzyć zestawy satelickie, Skompiluj projekt, a następnie Dodaj pliki jako dodatkowe zestawy za pomocą karty **Zaawansowane** **projektanta pakietów**. Podczas dodawania zestawów Dołącz [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] folder kultury do ścieżki lokalizacji, na przykład *DE-de \\ {Nazwa elementu projektu} .resources.dll*. Dzięki temu pakiet będzie zawierać pliki o tej samej nazwie.

 W kodzie Zastąp stałe kodowane ciągi wywołaniami <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metody przy użyciu następującej składni:

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 Aby uzyskać więcej informacji, zobacz [How to: lokalizowanie kodu](../sharepoint/how-to-localize-code.md).

#### <a name="web-part-code-localization"></a>Lokalizacja kodu części sieci Web
 Składniki Web Part zawierają funkcję niestandardowego edytora właściwości, która zawiera atrybuty kodu, które używają zakodowanych ciągów, takich jak WebDisplayName, Category i WebDescription. Aby zastąpić wartości ciągu dla tych atrybutów, utwórz oddzielną klasę, która dziedziczy z klasy atrybutu. W tych klasach ustaw właściwość atrybutu. Właściwość atrybutu zależy od klasy bazowej. Na przykład właściwość atrybutu WebDisplayName to DisplayNameValue, a właściwość atrybutu WebDescription to DescriptionValue.

 W klasie pochodnej odwołuje się do identyfikatora ciągu z pliku zasobów i obiektu ResourceManager, aby uzyskać zlokalizowaną wartość identyfikatora ciągu. Zwróć tę wartość do atrybutu edytora właściwości.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Lokalizowanie funkcji](../sharepoint/how-to-localize-a-feature.md)
- [Instrukcje: Lokalizowanie znacznika ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Instrukcje: lokalizowanie kodu](../sharepoint/how-to-localize-code.md)
- [Instrukcje: Dodawanie pliku zasobów](../sharepoint/how-to-add-a-resource-file.md)
- [Instrukcje: korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości i uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)

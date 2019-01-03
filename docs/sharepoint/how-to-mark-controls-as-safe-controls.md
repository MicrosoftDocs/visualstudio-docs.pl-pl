---
title: 'Instrukcje: Oznaczanie kontrolek pojęciem bezpiecznych kontrolek | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 87e99937239ad080d24bf997d6c2de2a5d8f73ac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989377"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Instrukcje: Oznaczanie kontrolek pojęciem bezpiecznych kontrolek
  Dla bezpieczeństwa SharePoint oddzieli kontrolki sieci Web, które są chronione przed uruchomienie skryptu kontrolki sieci Web, które nie są. Chronione formantów, lub *bezpiecznych kontrolek*, może zostać oceniony przez niezaufanym użytkownikom. Możesz oznaczyć kontrolek jako bezpiecznych właściwości wpisy bezpiecznych kontrolek elementu projektu programu SharePoint lub w **projektancie pakietu** po dodaniu zestawu do pakietu. Aby uzyskać więcej informacji, zobacz artykuł  
  
 [plik Web.config zmiana ustawień](http://go.microsoft.com/fwlink/?LinkId=178965) i [rejestrowanie zestaw części sieci Web jako bezpiecznej kontrolki](http://go.microsoft.com/fwlink/?LinkId=171013).  
  
> [!IMPORTANT]  
>  Te procedury są w celach ilustracyjnych. Oznaczanie kontrolek bezpieczne, tylko wtedy, gdy masz pewność, że są bezpieczne.  
  
## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Oznaczanie bezpiecznych kontrolek we właściwości wpisy kontroli bezpiecznego  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Aby oznaczyć kontrolek jako bezpiecznych lub niebezpieczne we właściwości wpisy kontroli bezpiecznego
  
1.  Tworzenie rozwiązań programu SharePoint w projekcie wizualny składnik Web Part.  
  
2.  Dodaj dwa formanty do składnika Web part: pole tekstowe i przycisk. Pozostaw nazwy wartości domyślnych, TextBox1 i Button1, odpowiednio.  
  
3.  Dodania dwóch wpisów do składnika Web part **wpisy bezpiecznych kontrolek** właściwości. Aby to zrobić, wybierz przycisk wielokropka (![elipsy projektanta Mobile ASP.NET](../sharepoint/media/mwellipsis.gif "elipsy projektanta Mobile ASP.NET")) znajdujący się obok **wpisy bezpiecznych kontrolek** właściwość  **Właściwości** okna.  
  
     **Wpisy bezpiecznych kontrolek** pojawi się okno dialogowe.  
  
4.  W **wpisy bezpiecznych kontrolek** okna dialogowego wybierz **Dodaj** przycisk dwa razy, aby dodać dwa wpisy bezpiecznych kontrolek do **członków** okienka: jeden dla przycisku i jeden dla pola tekstowego.  
  
5.  Wybierz pierwszy wpis bezpiecznej kontrolki, a następnie zmień wartość jego **bezpieczne** właściwości **False**, jego **nazwy typu** właściwość **Button1**, a jego **bezpieczne względem skryptu** właściwości **False**.  
  
     W tym kroku identyfikuje formant przycisku jako kontrolkę, która jest niebezpieczne.  
  
6.  Wybierz drugi wpis bezpiecznej kontrolki listy. Pozostaw wartość jego **bezpieczne** właściwość jako **True** i ustaw jego **nazwy typu** właściwości **TextBox1** i jego **bezpieczne Względem skryptu** właściwości **True**.  
  
     Formant pola tekstowego jest teraz oznaczone jako formant, który jest zabezpieczony przed uruchomienie skryptu.  
  
7.  Wybierz **OK** przycisk, aby zamknąć okno dialogowe.  
  
## <a name="marking-safe-controls-in-the-package-designer"></a>Oznaczanie bezpiecznych kontrolek w Projektancie pakietu  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Aby oznaczyć kontroluje jako bezpieczny lub niebezpiecznych w Projektancie pakietu
  
1.  Tworzenie rozwiązań programu SharePoint w projekcie wizualny składnik Web Part.  
  
2.  Dodaj dwa formanty do składnika Web part: pole tekstowe i przycisk. Pozostaw nazwy wartości domyślnych, TextBox1 i Button1, odpowiednio.  
  
     Zwróć uwagę na przestrzeń nazw formantu, ponieważ jest on używany później.  
  
3.  Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie** do skompilowania projektu.  
  
4.  Utwórz innego rozwiązania programu SharePoint.  
  
5.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla *Package.Package* , a następnie wybierz **Otwórz** otworzyć **projektancie pakietu**.  
  
6.  W **projektancie pakietu**, wybierz **zaawansowane** kartę.  
  
7.  W obszarze **dodatkowe zestawy**, wybierz **Dodaj** przycisk, a następnie wybierz **Dodaj istniejący zestaw** z listy.  
  
8.  W **Dodaj istniejący zestaw** okno dialogowe, wybierz przycisk wielokropka (![elipsy projektanta Mobile ASP.NET](../sharepoint/media/mwellipsis.gif "elipsy projektanta Mobile ASP.NET")) znajdujący się obok  **Ścieżka źródłowa**.  
  
9. Wybierz zestaw z rozwiązania programu SharePoint, który został utworzony w kroku 1, a następnie wybierz **Otwórz** przycisku.  
  
10. W tym przykładzie należy pozostawić **cel wdrożenia** opcji GlobalAssemblyCache.  
  
     Ten krok powoduje, że zestaw do wdrażania systemu globalnej pamięci podręcznej zestawów (GAC). Jeśli chcesz, aby zestaw do wdrażania sieci Web folderu aplikacji (Bin), wybierz tę opcję. Aby uzyskać więcej informacji, zobacz [wdrażania składników Web Part w SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. W **bezpiecznych kontrolek** wybierz **kliknij tutaj, aby dodać nowy element** przycisku.  
  
12. Wprowadź wartości dla właściwości z poniższej tabeli.  
  
    |Nazwa właściwości|Wartość|  
    |-------------------|-----------|  
    |Przestrzeń nazw|W pełni kwalifikowanych przestrzeni nazw kontrolki, takie jak **BdcModelProject1.VisualWebPart1**.|  
    |Nazwa typu|Button1|  
    |Nazwa zestawu|Zestawu silne nazwy, takie jak: Microsoft.Office.SharePoint.ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Bezpieczne|Wyczyść **bezpieczne** pole wyboru.|  
    |Bezpieczne względem skryptu|Pozostaw **bezpieczne względem skryptu** wyczyść pole wyboru.|  
  
    > [!NOTE]  
    >  **Nazwy zestawu** wartość dla zestawów dodane za pomocą **zaawansowane** karcie **projektancie pakietu** nie może być token, musi być silnej nazwy zestawu. Aby uzyskać więcej informacji, zobacz [tworzenie i zestawy Using Strong-Named](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Wybierz **kartę** klawisz, aby utworzyć inny wpis bezpiecznej kontrolki.  
  
14. Wybierz **kliknij tutaj, aby dodać nowy element** ponownie przycisk.  
  
15. Wprowadź wartości dla właściwości z poniższej tabeli.  
  
    |Nazwa właściwości|Wartość|  
    |-------------------|-----------|  
    |Przestrzeń nazw|W pełni kwalifikowanych przestrzeni nazw kontrolki, takie jak **BdcModelProject1.VisualWebPart1**.|  
    |Nazwa typu|TextBox1|  
    |Nazwa zestawu|Zestawu silne nazwy, takie jak: Microsoft.Office.SharePoint.ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Bezpieczne|Wybierz **bezpieczne** pole wyboru.|  
    |Bezpieczne względem skryptu|Wybierz **bezpieczne względem skryptu** pole wyboru.|  
  
16. Wybierz **kartę** klucza, a następnie wybierz **OK** przycisk, aby zamknąć okno dialogowe.  
  
## <a name="see-also"></a>Zobacz także
 [Podaj informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Pakiet rozwiązania i wdrażania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  

---
title: 'Instrukcje: Oznaczanie kontrolek jako bezpiecznych formantów | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd7ed13504d3d91f4239a8ea070454e1c31b1114
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016259"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Instrukcje: Oznaczanie kontrolek jako bezpiecznych formantów
  W celu zapewnienia bezpieczeństwa program SharePoint rozróżnia kontrolki sieci Web, które są chronione przed iniekcją skryptu i kontrolkami sieci Web, które nie są. Dostęp do formantów chronionych lub *bezpiecznych kontrolek*można uzyskać za pomocą niezaufanych użytkowników. Kontrolki można oznaczyć jako bezpieczne we właściwości wpisy kontroli bezpieczeństwa elementu projektu programu SharePoint lub w **projektancie pakietów** po dodaniu zestawu do pakietu. Aby uzyskać więcej informacji, zobacz

- [web.config zmianę ustawień plików](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) i [zarejestrowanie zestawu składnika Web Part jako bezpiecznej kontroli](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

> [!IMPORTANT]
> Te procedury są przeznaczone do celów informacyjnych. Oznacz formanty jako bezpieczne tylko wtedy, gdy masz pewność, że są one bezpieczne.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Oznaczanie bezpiecznych formantów we właściwości wpisy bezpiecznego sterowania

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Aby oznaczyć formanty jako bezpieczne lub niebezpieczne we właściwości wpisy dotyczące bezpiecznego sterowania

1. Utwórz rozwiązanie SharePoint za pomocą projektu wizualnego składnika Web Part.

2. Dodaj dwa kontrolki do składnika Web Part: pole tekstowe i przycisk. Pozostaw odpowiednio nazwy domyślne, TextBox1 i Button1.

3. Dodaj dwa wpisy do właściwości **wpisów bezpiecznego sterowania** częścią sieci Web. Aby to zrobić, wybierz przycisk wielokropka (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")) obok właściwości **bezpieczne wpisy kontroli** w oknie **Właściwości** .

     Zostanie wyświetlone okno dialogowe **bezpieczne wpisy kontroli** .

4. W oknie dialogowym **bezpieczne wpisy kontroli** kliknij dwukrotnie przycisk **Dodaj** , aby dodać dwa bezpieczne wpisy kontroli do okienka **elementy członkowskie** : jeden dla przycisku i jeden dla pola tekstowego.

5. Wybierz pierwszy wpis bezpiecznego sterowania, a następnie zmień wartość jego właściwości **Safe** na **false**, jej właściwość **type name** na **Button1**i **bezpieczną Właściwość Script** na wartość **false**.

     Ten krok identyfikuje formant Button jako niebezpieczną kontrolę.

6. Wybierz drugą pozycję bezpieczne sterowanie na liście. Pozostaw wartość swojej **bezpiecznej** właściwości jako **true** i ustaw jej właściwość **type name** na **TextBox1** i jej bezpieczną Właściwość **Script** na **wartość true**.

     Kontrolka pole tekstowe jest teraz oznaczona jako formant, który jest bezpieczny przed iniekcją skryptu.

7. Wybierz przycisk **OK** , aby zamknąć okno dialogowe.

## <a name="marking-safe-controls-in-the-package-designer"></a>Oznaczanie bezpiecznych kontrolek w projektancie pakietów

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Aby oznaczyć formanty jako bezpieczne lub niebezpieczne w projektancie pakietów

1. Utwórz rozwiązanie SharePoint za pomocą projektu wizualnego składnika Web Part.

2. Dodaj dwa kontrolki do składnika Web Part: pole tekstowe i przycisk. Pozostaw odpowiednio nazwy domyślne, TextBox1 i Button1.

     Zwróć uwagę na przestrzeń nazw kontrolki, ponieważ jest ona używana później.

3. Na pasku menu wybierz **kompilację**Kompiluj  >  **rozwiązanie** , aby skompilować projekt.

4. Utwórz kolejne rozwiązanie programu SharePoint.

5. W **Eksplorator rozwiązań**Otwórz menu skrótów dla pliku *Package. Package* , a następnie wybierz **Otwórz** , aby otworzyć **projektanta pakietów**.

6. W **projektancie pakietów**wybierz kartę **Zaawansowane** .

7. W obszarze **dodatkowe zestawy**wybierz przycisk **Dodaj** , a następnie wybierz pozycję **Dodaj istniejący zestaw** z listy.

8. W oknie dialogowym **Dodaj istniejący zestaw** wybierz przycisk wielokropka (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")) obok **ścieżki źródłowej**.

9. Wybierz zestaw z rozwiązania programu SharePoint, który został utworzony w kroku 1, a następnie wybierz przycisk **Otwórz** .

10. Na potrzeby tego przykładu pozostaw opcję **cel wdrożenia** jako GlobalAssemblyCache.

     Ten krok powoduje wdrożenie zestawu w globalnej pamięci podręcznej zestawów (GAC) systemu. Jeśli chcesz, aby zestaw został wdrożony w folderze aplikacji sieci Web (bin), zaznacz tę opcję. Aby uzyskać więcej informacji, zobacz [wdrażanie składniki Web Part w programie SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

11. W polu **bezpieczne formanty** wybierz przycisk **kliknij tutaj, aby dodać nowy element** .

12. Wprowadź wartości właściwości z poniższej tabeli.

    |Nazwa właściwości|Wartość|
    |-------------------|-----------|
    |Przestrzeń nazw|W pełni kwalifikowana przestrzeń nazw dla kontrolki, na przykład **BdcModelProject1. VisualWebPart1**.|
    |Nazwa typu|Button1|
    |Nazwa zestawu|Silna nazwa zestawu, na przykład: Microsoft. Office. SharePoint. ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Sejf|Wyczyść pole wyboru **bezpieczne** .|
    |Bezpieczna przed skryptami|Pozostaw wyczyść pole wyboru **bezpieczne względem skryptu** .|

    > [!NOTE]
    > Wartość **nazwy zestawu** dla zestawów dodawanych za pomocą karty **Zaawansowane** **projektanta pakietów** nie może być tokenem, musi to być zestaw o silnej nazwie. Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie zestawów o silnej nazwie](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100)).

13. Wybierz klawisz **Tab** , aby utworzyć inny bezpieczny wpis kontroli.

14. Wybierz ponownie przycisk **kliknij tutaj, aby dodać nowy element** .

15. Wprowadź wartości właściwości z poniższej tabeli.

    |Nazwa właściwości|Wartość|
    |-------------------|-----------|
    |Przestrzeń nazw|W pełni kwalifikowana przestrzeń nazw dla kontrolki, na przykład **BdcModelProject1. VisualWebPart1**.|
    |Nazwa typu|TextBox1|
    |Nazwa zestawu|Silna nazwa zestawu, na przykład: Microsoft. Office. SharePoint. ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Sejf|Zaznacz pole wyboru **bezpieczne** .|
    |Bezpieczna przed skryptami|Zaznacz pole wyboru **bezpieczny względem skryptu** .|

16. Wybierz klawisz **Tab** , a następnie wybierz przycisk **OK** , aby zamknąć okno dialogowe.

## <a name="see-also"></a>Zobacz także
- [Udostępnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

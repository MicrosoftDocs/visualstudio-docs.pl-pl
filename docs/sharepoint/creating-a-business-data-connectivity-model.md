---
title: Tworzenie modelu łączności danych biznesowych | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bcfac4855320f420f2f123568498957ad8d84814
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863971"
---
# <a name="create-a-business-data-connectivity-model"></a>Tworzenie modelu łączności danych biznesowych
  Można Tworzenie modelu łączności danych biznesowych (BDC) lub dostosować istniejący model usługi łączności danych biznesowych przy użyciu programu Visual Studio. Każdy projekt programu SharePoint może zawierać tylko jeden model. Aby uzyskać więcej informacji, zobacz [integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="create-a-new-model"></a>Utwórz nowy model
 Aby utworzyć nowy model, Utwórz **Model usługi łączności danych biznesowych** projektu lub dodać **Model usługi łączności danych biznesowych** elementu do **pusty projekt programu SharePoint**.  
  
> [!NOTE]  
>  Konieczne jest posiadanie [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zainstalowana na danym komputerze.  
  
 Visual Studio dodaje folder do projektu. Ten folder zawiera nazwę która jest określona dla **Model usługi łączności danych biznesowych** pozycja **Dodaj nowy element** okno dialogowe. Jeśli tworzysz nową **Model usługi łączności danych biznesowych** projektu, Visual Studio nazwy folderu **BdcModel1**.  
  
 Program Visual Studio dodaje następujące pliki do nowego folderu:  
  
|Plik|Opis|  
|----------|-----------------|  
|Plik definicji modelu|Zawiera kod XML, który określa jednostki, metody, obiekty systemowe Line of Business (LOB) i innych metadanych, który opisuje model.<br /><br /> Modyfikowanie metadanych, w tym pliku przy użyciu projektanta łączności danych biznesowych **Eksplorator BDC**, **szczegóły metody BDC** oknie i **właściwości** okna.|  
|Pliku kodu usługi jednostki|Zawiera metody, które pobierać, aktualizować i usuwać wystąpień jednostki domyślnej.|  
  
 Aby zdefiniować właściwości jednostki, przeprowadź edycję pliku kodu jednostki. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Aby pobrać, aktualizować i usuwać wystąpień jednostki, Dodaj kod do pliku kodu usługi jednostki. Aby uzyskać więcej informacji, zobacz [projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Podczas kompilowania projektu programu Visual Studio tworzy zestaw. Upewnij się, że nie należy dodawać innych elementów do projektu, który Dodaj kod, aby zestaw projektu (na przykład: **sekwencyjnego przepływu pracy** elementu lub **składnika Web Part** elementu). Kod dla tego elementu nie będzie działać w przypadku wdrażania rozwiązania, ponieważ pakiet rozwiązania nie kopiuje zestawu do globalnej pamięci podręcznej.  Pakiet rozwiązania wdraża zestaw usługi łączności danych biznesowych tylko na bazę danych w programie SharePoint.  
  
> [!NOTE]  
>  Program Visual Studio kopiuje zestawu do obu lokalizacjach na komputerze lokalnym podczas debugowania projektu.  
  
## <a name="add-an-existing-model"></a>Dodawanie istniejącego modelu
 Można zaimportować modelu, który został utworzony przy użyciu innych narzędzi, takich jak SharePoint Designer. Można także zaimportować istniejący model do projektu w następujących sytuacjach:  
  
- Aby dostosować model, który jest już wdrożony do farmy serwerów programu SharePoint.  
  
- Do pakietu i wdrożenie istniejącego modelu wielu farm serwerów programu SharePoint.  
  
  W obu przypadkach systemami LOB, zdefiniowane w modelu, który można zaimportować nie ulegają zmianom i będą nadal działać zgodnie z oczekiwaniami. Aby dodać istniejący model do projektu programu SharePoint, należy użyć programu Visual Studio **Dodaj istniejący element** okno dialogowe. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie istniejącego modelu BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
  Systemem LOB, typ zestawu .NET Framework można dodać do importowanych modelu, wybierając opcję **element LobSystem zestawu .NET Dodawanie**. Dzięki temu można pisać kod niestandardowy i zdefiniuj metadanych dla importowanego modelu za pomocą projektanta.  
  
## <a name="related-topics"></a>Tematy pokrewne
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Tworzenie modelu BDC](../sharepoint/how-to-create-a-bdc-model.md)|Dowiesz się, jak utworzyć nowy model usługi łączności danych biznesowych.|  
|[Instrukcje: Dodawanie istniejącego modelu BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Dowiesz się, jak zaimportować istniejący model do projektu programu SharePoint.|  
|[Instrukcje: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości oraz uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|W tym artykule opisano, jak zapewnić ciągów, które są łączone ze sobą przy użyciu metadanych modelu, gdy model jest używane przez składnik Web Part lub strony sieci Web.|  
|[Instrukcje: Dołączanie niestandardowego zestawu w funkcji BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Dowiesz się, jak Dołączanie niestandardowego zestawu w funkcji.|  

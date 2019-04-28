---
title: Stosowanie modułów podczas dołączania plików w rozwiązaniu | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 569f1027163d5651d184254b4e6f57a02df2a39a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007844"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Użyj modułów, aby uwzględnić pliki w rozwiązaniu
  Mogą wystąpić sytuacje, kiedy warto wdrożyć pliki do serwera programu SharePoint, niezależnie od ich typu pliku, na przykład nowe strony wzorcowej. Aby to zrobić, można użyć *modułów* (nie należy mylić z [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modułów kodu). Moduły są kontenerami dla plików w rozwiązaniu programu SharePoint. Po wdrożeniu rozwiązania plików w module są kopiowane do określonych folderów na serwerze programu SharePoint.

## <a name="module-items-and-elements"></a>Moduł elementów i elementów
 Aby utworzyć moduł, dodaj go do projektu, wybierając je w **Dodaj nowy element** okno dialogowe. Następnie należy zmodyfikować jego *Elements.xml* pliku, aby uwzględnić nazwy plików, którą chcesz wdrożyć, gdzie znajdują się w systemie, a powinny zostać skopiowane na serwerze programu SharePoint.

 Oto przykład *Elements.xml* pliku modułu:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Nowo utworzony moduły zawierają następujące domyślne pliki:

|Nazwa pliku|Opis|
|---------------|-----------------|
|*Elements.xml*|Plik definicji modułu.|
|*Przykład.txt*|Plik zastępczy, który stanowi przykład pliku w module.|

 *Elements.xml* plik zawiera następujące elementy:

|Nazwa elementu|Opis|
|------------------|-----------------|
|Elementy|Zawiera wszystkie elementy zdefiniowane w module.|
|Moduł|Element modułu ma jeden atrybut *nazwa*, który określa nazwę modułu w formacie `<Module Name="Module1">`.<br /><br /> Należy pamiętać, że jeśli zmienisz nazwę modułu (lub jego *nazwa folderu* właściwości), należy ręcznie zaktualizować nazwy w elemencie modułu.<br /><br /> Jeśli określisz podkatalogu dla plików w elemencie modułu [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) automatycznie utworzy pasującego strukturę katalogów dla nich.|
|Plik|Element plików ma dwa parametry *ścieżki* i *adresu Url*.<br /><br /> -Path: Nazwa i lokalizacja pliku rozwiązania programu SharePoint. Ten format jest, `Path="Module1\Sample.txt"`.<br /><br /> — Adres Url: Lokalizacja, w której plik zostanie wdrożony na serwerze programu SharePoint. Ten format jest, `Url="Module1/Sample.txt"`.<br /><br /> -Type: Opcjonalny atrybut, który ma dwa ustawienia: *GhostableInLibrary* i *Ghostable*. Ten format jest, `Type="GhostableInLibrary"`. Określanie *GhostableInLibrary* oznacza, że plik zostanie dodany do biblioteki dokumentów programu SharePoint wraz z elementu listy, aby dołączyć plik, gdy zostanie dodany do biblioteki. Określanie *Ghostable* powoduje, że plik ma zostać dodany do programu SharePoint spoza biblioteki dokumentów.|

 Każdy plik, który chcesz wdrożyć, wymaga oddzielnego `<File>` element wpisu w *Elements.xml*.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dołączanie plików za pomocą modułu](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Jak: Aprowizowanie pliku](http://go.microsoft.com/fwlink/?LinkID=144271)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Tworzenie składników web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

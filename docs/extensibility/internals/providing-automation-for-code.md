---
title: Dostarczanie automatyzacji dla kodu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd13b7db2065069ff1540dbfc921570c2b230b8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705990"
---
# <a name="providing-automation-for-code"></a>Zapewnianie automatyzacji kodu
Tworzenie modelu automatyzacji dla kodu nie jest wymagane. Zestaw SDK środowiska nie dostarcza przykładu do tego celu. Aby uzyskać wgląd w modele kodu, zapoznaj się z <xref:EnvDTE.CodeModel> obiektem.

 Aby zaimplementować model kodu, należy zaimplementować wszystkie interfejsy, które są określone przez wewnętrzną strukturę danych. Obiekty muszą pochodzić od `IDispatch` klasy.

 Obiekty, które można rozłożyć <xref:EnvDTE.CodeModel> , <xref:EnvDTE.FileCodeModel> są dostępne z obiektu i <xref:EnvDTE.Project> wyglądać następująco:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Można wybrać opcję implementacji tylko `CodeModel` `FileCodeModel` interfejsu lub w obiekcie zwracanym z `Project` <xref:EnvDTE.ProjectItem> obiektów i. Podaj wszelkie funkcje z tego interfejsu, które są odpowiednie dla Twojego systemu projektu.

 Jeśli chcesz dodać funkcje, takie jak metody lub właściwości, które nie są dostępne ze standardowego `CodeModel` i `FileCodeModel` interfejsów, Utwórz własny interfejs, który dziedziczy ze standardowego. Upewnij się, że dokument został udokumentowany w systemie projektu, aby użytkownicy końcowi wiedzieli, że zobaczysz ją. Można zwrócić standardowy interfejs, ale użytkownik może wywołać `QueryInterface` metodę lub rzutowanie do interfejsu, jeśli wiadomo, że istnieje.

## <a name="see-also"></a>Zobacz też
- [Omówienie modelu automatyzacji](../../extensibility/internals/automation-model-overview.md)

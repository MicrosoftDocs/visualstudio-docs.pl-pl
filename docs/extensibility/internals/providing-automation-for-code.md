---
title: Dostarczanie automatyzacji dla kodu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 874446aa6bf2e40a120aac49e7d91fd3d861d1d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724962"
---
# <a name="providing-automation-for-code"></a>Zapewnianie automatyzacji kodu
Tworzenie modelu automatyzacji dla kodu nie jest wymagane. Zestaw SDK środowiska nie dostarcza przykładu do tego celu. Aby uzyskać wgląd w modele kodu, zobacz <xref:EnvDTE.CodeModel> obiektu.

 Aby zaimplementować model kodu, należy zaimplementować wszystkie interfejsy, które są określone przez wewnętrzną strukturę danych. Obiekty muszą pochodzić z klasy `IDispatch`.

 Obiekty, które można rozciągnąć, <xref:EnvDTE.CodeModel> i <xref:EnvDTE.FileCodeModel>, są dostępne z obiektu <xref:EnvDTE.Project> i wyglądają następująco:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Można wybrać opcję implementacji tylko `CodeModel` lub interfejs `FileCodeModel` w obiekcie zwracanym z `Project` i <xref:EnvDTE.ProjectItem> obiektów. Podaj wszelkie funkcje z tego interfejsu, które są odpowiednie dla Twojego systemu projektu.

 Jeśli chcesz dodać funkcje, takie jak metody lub właściwości, które nie są dostępne w standardowych `CodeModel` i `FileCodeModel` interfejsy, Utwórz własny interfejs, który dziedziczy ze standardowego. Upewnij się, że dokument został udokumentowany w systemie projektu, aby użytkownicy końcowi wiedzieli, że zobaczysz ją. Można zwrócić standardowy interfejs, ale użytkownik może wywołać metodę `QueryInterface` lub rzutowanie do interfejsu, jeśli istnieje.

## <a name="see-also"></a>Zobacz także
- [Omówienie modelu automatyzacji](../../extensibility/internals/automation-model-overview.md)
---
UID: NN:dbgmodel.IDataModelNameBinder
title: IDataModelNameBinder (dbgmodel.h)
description: Interface to a name binder – a component which can associate names in a context with objects or symbols.
ms.date: 07/13/2018
keywords: ["IDataModelNameBinder interface"]
req.header: dbgmodel.h
req.include-header: 
req.target-type: 
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
targetos: Windows
tech.root: debugger
ms.custom: RS5
f1_keywords:
 - IDataModelNameBinder
 - dbgmodel/IDataModelNameBinder
topic_type:
 - apiref
api_type:
 - COM
api_location:
 - dbgmodel.h
api_name:
 - IDataModelNameBinder
---

# IDataModelNameBinder interface


## -description

Interface to a name binder – a component which can associate names in a context with objects or symbols.

The default name binder for script providers.

## -inheritance

IDataModelNameBinder inherits from IUnknown.

## -remarks

The data model provides a standard way for script providers to determine the meaning of a given name in a given context (e.g.: determining what bar means for foo.bar) that will operate across a variety of script providers. This mechanism is known as a name binder and is represented by the IDataModelNameBinder interface. Such a binder encapsulates a set of rules about how the name resolves and how to deal with conflict resolution where a name is defined multiple times on an object. Part of these rules include things such as how a projected name (one added by a data model) resolves against a native name (one in the type system of the language being debugged). 

In order to provide a degree of consistency across script providers, the data model's script manager provides a default name binder. This default name binder can be acquired via a call to the GetDefaultNameBinder method on the [IDataModelScriptManager](nn-dbgmodel-idatamodelscriptmanager.md) interface.

## -see-also

[Debugger Data Model C++ Overview](/windows-hardware/drivers/debugger/data-model-cpp-overview)

# === This file is part of Calamares - <https://calamares.io> ===
#
#   SPDX-FileCopyrightText: 2020 Adriaan de Groot <groot@kde.org>
#   SPDX-License-Identifier: BSD-2-Clause
#
include_directories(${PROJECT_BINARY_DIR}/src/libcalamaresui)
calamares_add_plugin(summary
    TYPE viewmodule
    EXPORT_MACRO PLUGINDLLEXPORT_PRO
    SOURCES
        Config.cpp
        SummaryModel.cpp
        SummaryPage.cpp
        SummaryViewStep.cpp
    UI
    SHARED_LIB
    NO_CONFIG
)

set(REDALERT_SRC
    lcwcomp.asm
    txtprnt.asm
    keyfbuff.asm
    _wsproto.cpp
    2keyfram.cpp
    aadata.cpp
    abstract.cpp
    adata.cpp
    aircraft.cpp
    anim.cpp
    audio.cpp
    b64pipe.cpp
    b64straw.cpp
    bar.cpp
    base.cpp
    base64.cpp
    bbdata.cpp
    bdata.cpp
    bench.cpp
    bfiofile.cpp
    bigcheck.cpp
    blowfish.cpp
    blowpipe.cpp
    blwstraw.cpp
    buff.cpp
    building.cpp
    bullet.cpp
    cargo.cpp
    carry.cpp
    ccfile.cpp
    ccini.cpp
    ccmpath.cpp
    ccptr.cpp
    ccten.cpp
    cdata.cpp
    cdfile.cpp
    cell.cpp
    checkbox.cpp
    cheklist.cpp
    colrlist.cpp
    combat.cpp
    combuf.cpp
    comqueue.cpp
    confdlg.cpp
    connect.cpp
    conquer.cpp
    const.cpp
    control.cpp
    coord.cpp
    crate.cpp
    crc.cpp
    crcpipe.cpp
    crcstraw.cpp
    credits.cpp
    crew.cpp
    cstraw.cpp
    debug.cpp
    descdlg.cpp
    dial8.cpp
    dialog.cpp
    dibfile.cpp
    dibutil.cpp
    display.cpp
    door.cpp
    drive.cpp
    drop.cpp
    dynavec.cpp
    edit.cpp
    egos.cpp
    ending.cpp
    event.cpp
    expand.cpp
    face.cpp
    facing.cpp
    factory.cpp
    findpath.cpp
    fixed.cpp
    flasher.cpp
    fly.cpp
    foot.cpp
    fuse.cpp
    gadget.cpp
    gamedlg.cpp
    gauge.cpp
    globals.cpp
    goptions.cpp
    gscreen.cpp
    hdata.cpp
    heap.cpp
    help.cpp
    house.cpp
    hsv.cpp
    iconlist.cpp
    idata.cpp
    infantry.cpp
    ini.cpp
    inibin.cpp
    inicode.cpp
    init.cpp
    int.cpp
    interpal.cpp
    intro.cpp
    iomap.cpp
    ioobj.cpp
    ipx.cpp
    ipx95.cpp
    ipxaddr.cpp
    ipxconn.cpp
    ipxgconn.cpp
    ipxmgr.cpp
    jshell.cpp
    key.cpp
    layer.cpp
    lcw.cpp
    lcwpipe.cpp
    lcwstraw.cpp
    lcwuncmp.cpp
    link.cpp
    list.cpp
    loaddlg.cpp
    logic.cpp
    lzo1x_c.cpp
    lzo1x_d.cpp
    lzopipe.cpp
    lzostraw.cpp
    lzw.cpp
    lzwpipe.cpp
    lzwstraw.cpp
    map.cpp
    mapeddlg.cpp
    mapedit.cpp
    mapedplc.cpp
    mapedsel.cpp
    mapedtm.cpp
    mapsel.cpp
    mci.cpp
    mcimovie.cpp
    menus.cpp
    miscasm.cpp
    mission.cpp
    mixfile.cpp
    monoc.cpp
    mouse.cpp
    mp.cpp
    mpgset.cpp
    mplayer.cpp
    mpmgrw.cpp
    mpu.cpp
    msgbox.cpp
    msglist.cpp
    netdlg.cpp
    object.cpp
    odata.cpp
    options.cpp
    overlay.cpp
    palettec.cpp
    pipe.cpp
    pk.cpp
    pkpipe.cpp
    pkstraw.cpp
    power.cpp
    profile.cpp
    queue.cpp
    radar.cpp
    radio.cpp
    ramfile.cpp
    rand.cpp
    random.cpp
    rawolapi.cpp
    readline.cpp
    reinf.cpp
    rgb.cpp
    rndstraw.cpp
    rotbmp.cpp
    rules.cpp
    saveload.cpp
    scenario.cpp
    score.cpp
    scroll.cpp
    sdata.cpp
    seditdlg.cpp
    sendfile.cpp
    seqconn.cpp
    session.cpp
    sha.cpp
    shape.cpp
    shapebtn.cpp
    shapipe.cpp
    shastraw.cpp
    sidebar.cpp
    slider.cpp
    smudge.cpp
    sounddlg.cpp
    special.cpp
    stamp.asm
    sprite.cpp
    startup.cpp
    statbtn.cpp
    stats.cpp
    straw.cpp
    super.cpp
    surface.cpp
    tab.cpp
    taction.cpp
    target.cpp
    tcpip.cpp
    tdata.cpp
    team.cpp
    teamtype.cpp
    techno.cpp
    template.cpp
    tenmgr.cpp
    terrain.cpp
    tevent.cpp
    textbtn.cpp
    theme.cpp
    toggle.cpp
    tooltip.cpp
    tracker.cpp
    trigger.cpp
    trigtype.cpp
    txtlabel.cpp
    udata.cpp
    udpaddr.cpp
    unit.cpp
    utracker.cpp
    vdata.cpp
    vector.cpp
    version.cpp
    vessel.cpp
    visudlg.cpp
    vortex.cpp
    w95trace.cpp
    warhead.cpp
    weapon.cpp
    iconset.cpp
    winstub.cpp
    wolapiob.cpp
    woledit.cpp
    wolstrng.cpp
    wol_cgam.cpp
    wol_chat.cpp
    wol_dnld.cpp
    wol_gsup.cpp
    wol_logn.cpp
    wol_main.cpp
    wol_opt.cpp
    wsproto.cpp
    wspudp.cpp
    xpipe.cpp
    xstraw.cpp
)

if(CMAKE_CONFIGURATION_TYPES)
    # Glob all the header files together to add to the project for msvc/xcode.
    # Not ideal as CMake won't notice if you add any until something else prompts a CMake run
    # but this is largely a convenience feature for MSVC/XCode users.
    file(GLOB_RECURSE REDALERT_HEADERS "*.h")
    set(_REDALERT_SOURCES ${REDALERT_SRC})

    foreach(_REDALERT_SOURCE IN ITEMS ${_REDALERT_SOURCES})
        get_filename_component(_REDALERT_SOURCE_PATH "${_REDALERT_SOURCE}" PATH)
        string(REPLACE "${CMAKE_CURRENT_SOURCE_DIR}" "" _REDALERT_GROUP_PATH "${_REDALERT_SOURCE_PATH}")
        string(REPLACE "/" "\\" _REDALERT_GROUP_PATH "${_REDALERT_GROUP_PATH}")
        source_group("Source Files\\${_REDALERT_GROUP_PATH}" FILES "${_REDALERT_SOURCE}")
    endforeach()

    foreach(_REDALERT_HEADER IN ITEMS ${REDALERT_HEADERS})
        get_filename_component(_REDALERT_HEADER_PATH "${_REDALERT_HEADER}" PATH)
        string(REPLACE "${CMAKE_CURRENT_SOURCE_DIR}" "" _REDALERT_HGROUP_PATH "${_REDALERT_HEADER_PATH}")
        string(REPLACE "/" "\\" _REDALERT_HGROUP_PATH "${_REDALERT_HGROUP_PATH}")
        source_group("Header Files\\${_REDALERT_HGROUP_PATH}" FILES "${_REDALERT_HEADER}")
    endforeach()
endif()

if(BUILD_REMASTERRA)
    add_library(RedAlert SHARED 
        dllinterface.cpp
        dllinterfaceeditor.cpp
        sidebarglyphx.cpp
        ${REDALERT_SRC}
        ${REDALERT_HEADERS}
    )
    target_compile_definitions(RedAlert PUBLIC $<$<CONFIG:Debug>:_DEBUG> ${REMASTER_DEFS})
    target_include_directories(RedAlert PUBLIC ${CMAKE_SOURCE_DIR} .)
    target_link_libraries(RedAlert commonr ${REMASTER_LIBS} ${STATIC_LIBS})
    set_target_properties(RedAlert PROPERTIES PREFIX "")
endif()

if(BUILD_VANILLARA)
    add_executable(VanillaRA ${REDALERT_SRC} ${REDALERT_HEADERS})
    target_compile_definitions(VanillaRA PUBLIC $<$<CONFIG:Debug>:_DEBUG> ${VANILLA_DEFS})
    target_include_directories(VanillaRA PUBLIC ${CMAKE_SOURCE_DIR} .)
    target_link_libraries(VanillaRA commonv ${VANILLA_LIBS} ${STATIC_LIBS})
    set_target_properties(VanillaRA PROPERTIES OUTPUT_NAME vanillara)
    if(MAP_EDITORRA)
        target_compile_definitions(VanillaRA PUBLIC INTERNAL_VERSION)
    endif()
    if(NETWORKING)
        target_compile_definitions(VanillaRA PUBLIC WINSOCK_IPX)
    endif()
    # Control if we auto generate a console and which "main" function we link using MSVC.
    if(MSVC)
        set_target_properties(VanillaRA PROPERTIES LINK_FLAGS "/subsystem:windows /ENTRY:WinMainCRTStartup")
    endif()
endif()
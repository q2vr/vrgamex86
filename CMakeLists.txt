set(GAME_SOURCES
    ../qcommon/shared/m_flash.c
    ../qcommon/shared/q_shared.c
    ../qcommon/murmur3/murmur3.c
    acesrc/acebot_ai.c
    acesrc/acebot_cmds.c
    acesrc/acebot_compress.c
    acesrc/acebot_items.c
    acesrc/acebot_movement.c
    acesrc/acebot_nodes.c
    acesrc/acebot_spawn.c
    g_ai.c
    g_camera.c
    g_chase.c
    g_cmds.c
    g_combat.c
    g_crane.c
    g_ctf.c
    g_fog.c
    g_func.c
    g_items.c
    g_jetpack.c
    g_lights.c
    g_lock.c
    g_main.c
    g_misc.c
    g_model.c
    g_monster.c
    g_moreai.c
    g_mtrain.c
    g_patchplayermodels.c
    g_pendulum.c
    g_phys.c
    g_reflect.c
    g_save.c
    g_spawn.c
    g_svcmds.c
    g_target.c
    g_thing.c
    g_tracktrain.c
    g_trigger.c
    g_turret.c
    g_utils.c
    g_vehicle.c
    g_weapon.c
    km_cvar.c
    monster/m_actor.c
    monster/m_actor_weap.c
    monster/m_berserk.c
    monster/m_boss2.c
    monster/m_boss3.c
    monster/m_boss31.c
    monster/m_boss32.c
    monster/m_brain.c
    monster/m_chick.c
    monster/m_flipper.c
    monster/m_float.c
    monster/m_flyer.c
    monster/m_gladiator.c
    monster/m_gunner.c
    monster/m_hover.c
    monster/m_infantry.c
    monster/m_insane.c
    monster/m_medic.c
    monster/m_move.c
    monster/m_mutant.c
    monster/m_parasite.c
    monster/m_soldier.c
    monster/m_supertank.c
    monster/m_tank.c
    player/p_chase.c
    player/p_client.c
    player/p_hud.c
    player/p_menu.c
    player/p_text.c
    player/p_trail.c
    player/p_view.c
    player/p_weapon.c
)

set(GAME_HEADERS
	../qcommon/shared/q_shared.h
	../qcommon/shared/game.h
	acesrc/acebot.h
	g_ctf.h
	g_local.h
	km_cvar.h
	laz_misc.h
	monster/m_actor.h
	monster/m_berserk.h
	monster/m_boss2.h
	monster/m_boss31.h
	monster/m_boss32.h
	monster/m_brain.h
	monster/m_chick.h
	monster/m_flipper.h
	monster/m_float.h
	monster/m_flyer.h
	monster/m_gladiator.h
	monster/m_gunner.h
	monster/m_hover.h
	monster/m_infantry.h
	monster/m_insane.h
	monster/m_medic.h
	monster/m_mutant.h
	monster/m_parasite.h
	monster/m_player.h
	monster/m_rider.h
	monster/m_soldier.h
	monster/m_supertank.h
	monster/m_tank.h
	pak.h
	player/p_menu.h
	player/p_text.h
	resource.h
	tables/clientfields.h
	tables/fields.h
	tables/gamefunc_decs.h
	tables/gamefunc_list.h
	tables/gamemmove_decs.h
	tables/gamemmove_list.h
	tables/levelfields.h
)

# check 64 bit
# this will break on non-x86 processors
if( CMAKE_SIZEOF_VOID_P EQUAL 4 )
	set( ARCH "x86" )
else()
	set(  ARCH "x64" )
endif()

# add_definitions(-DDISABLE_FOG)
add_library(game MODULE ${GAME_SOURCES} ${GAME_HEADERS})
set_target_properties(game PROPERTIES PREFIX "" OUTPUT_NAME "vrgame${ARCH}")
set_target_properties(game PROPERTIES XCODE_ATTRIBUTE_OTHER_CFLAGS[variant=Debug] "-D_DEBUG" )

target_compile_options(game PRIVATE -fvisibility=hidden)

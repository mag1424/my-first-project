# my-first-project
# Ground forces class represents troops and vehicles for attacking opponents
class GroundForces:
    def __init__(self, rank, number_of_troops):
        self.rank = rank
        self.number_of_troops = number_of_troops
        self.health = 100 * rank
        self.vehicle_health = 1000  # Adjusted attribute name for consistency

    def __repr__(self):
        return f"Rank: {self.rank}, Troops: {self.number_of_troops}, Health: {self.health}, Vehicle Health: {self.vehicle_health}"

class Vehicles:
    def __init__(self, vehicle, tanks, number_of_vehicles, number_of_tanks):
        self.vehicle = vehicle
        self.tanks = tanks
        self.number_of_vehicles = number_of_vehicles
        self.number_of_tanks = number_of_tanks

    def __repr__(self):
        return f"Vehicles: {self.vehicle} x {self.number_of_vehicles}, Tanks: {self.tanks} x {self.number_of_tanks}"

class Navy:
    def __init__(self, level, number_of_boats, type_of_navy):
        self.level = level
        self.number_of_boats = number_of_boats
        self.type_of_navy = type_of_navy

    def __repr__(self):
        return f"Level: {self.level}, Boats: {self.number_of_boats}, Type: {self.type_of_navy}"

class AirForces:
    def __init__(self, number_of_airplane, type_of_airplane):
        self.number_of_airplane = number_of_airplane
        self.type_of_airplane = type_of_airplane

    def __repr__(self):
        return f"Airplanes: {self.number_of_airplane}, Type: {self.type_of_airplane}"

class AirDefense:
    def __init__(self, number_of_airdefense, type_of_airdefense):
        self.number_of_airdefense = number_of_airdefense
        self.type_of_airdefense = type_of_airdefense

    def __repr__(self):
        return f"Air Defense Systems: {self.number_of_airdefense}, Type: {self.type_of_airdefense}"

class MissileForces:
    def __init__(self, number_of_missile, type_of_missile):
        self.number_of_missile = number_of_missile
        self.type_of_missile = type_of_missile

    def __repr__(self):
        return f"Missiles: {self.number_of_missile}, Type: {self.type_of_missile}"

# Player class represents the player who owns the various military forces
class Player:
    def __init__(self, player_name, ground_forces, navy, air_forces, air_defense, missile_forces):
        self.player_name = player_name
        self.ground_forces = ground_forces
        self.navy = navy
        self.air_forces = air_forces
        self.air_defense = air_defense
        self.missile_forces = missile_forces

    def __repr__(self):
        return (f"Player: {self.player_name}\n"
                f"Ground Forces: {self.ground_forces}\n"
                f"Navy: {self.navy}\n"
                f"Air Forces: {self.air_forces}\n"
                f"Air Defense: {self.air_defense}\n"
                f"Missile Forces: {self.missile_forces}")

# Battle class manages the interaction between two players
class Battle:
    def __init__(self, player_1, player_2):
        self.player_1 = player_1
        self.player_2 = player_2

    def attack(self, attacker, defender):
        # Example attack logic: reduce the defender's ground forces health
        defender.ground_forces.health -= 50
        print(f"{attacker.player_name} attacked {defender.player_name}! {defender.player_name}'s ground forces health is now {defender.ground_forces.health}.")

    def __repr__(self):
        return f"Battle between {self.player_1.player_name} and {self.player_2.player_name}"

# Example usage and interaction loop:
if __name__ == "__main__":
    # Create forces for Player 1
    ground_forces_1 = GroundForces(rank=3, number_of_troops=100)
    vehicles_1 = Vehicles(vehicle='Jeep', tanks='Abrams', number_of_vehicles=10, number_of_tanks=5)
    navy_1 = Navy(level=2, number_of_boats=15, type_of_navy='Destroyer')
    air_forces_1 = AirForces(number_of_airplane=10, type_of_airplane='F-15')
    air_defense_1 = AirDefense(number_of_airdefense=5, type_of_airdefense='Patriot')
    missile_forces_1 = MissileForces(number_of_missile=5, type_of_missile='Ballistic')

    player_1 = Player('Player 1', ground_forces_1, navy_1, air_forces_1, air_defense_1, missile_forces_1)

    # Create forces for Player 2
    ground_forces_2 = GroundForces(rank=2, number_of_troops=80)
    vehicles_2 = Vehicles(vehicle='Humvee', tanks='T-90', number_of_vehicles=8, number_of_tanks=3)
    navy_2 = Navy(level=1, number_of_boats=10, type_of_navy='Frigate')
    air_forces_2 = AirForces(number_of_airplane=8, type_of_airplane='MiG-29')
    air_defense_2 = AirDefense(number_of_airdefense=4, type_of_airdefense='S-300')
    missile_forces_2 = MissileForces(number_of_missile=3, type_of_missile='Cruise')

    player_2 = Player('Player 2', ground_forces_2, navy_2, air_forces_2, air_defense_2, missile_forces_2)

    battle = Battle(player_1, player_2)

    # Display initial player states
    print(player_1)
    print(player_2)

    # Simple loop for interaction
    while True:
        # Get user input to perform an action
        action = input("Enter '1' for Player 1 to attack Player 2, '2' for Player 2 to attack Player 1, or 'q' to quit: ").strip()

        if action == '1':
            battle.attack(player_1, player_2)
        elif action == '2':
            battle.attack(player_2, player_1)
        elif action.lower() == 'q':
            print("Exiting the game.")
            break
        else:
            print("Invalid input, please try again.")

        # Show updated player states
        print(player_1)
        print(player_2)
